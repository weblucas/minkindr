cmake_minimum_required(VERSION 2.8.3)
project(minkindr)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

find_package(Threads)
if (CATKIN_ENABLE_TESTING)
	catkin_add_gtest(${PROJECT_NAME}_tests 
	  test/test-main.cc
	  test/test-rotation.cc
	  test/test-sim3.cc
	  test/test-transformation.cc
	  test/test-transformation-2d.cc
	)


target_link_libraries(${PROJECT_NAME}_tests ${catkin_LIBRARIES} 
                                            ${CMAKE_THREAD_LIBS_INIT})

endif() #CATKIN_ENABLE_TESTING

# Add all files to show up in QtCreator.
FILE(GLOB_RECURSE LibFiles "include/*")
add_custom_target(headers SOURCES ${LibFiles})

cs_install()
cs_export()

