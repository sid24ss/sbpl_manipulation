cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

#Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
set(ROS_BUILD_TYPE Debug)

# Add a ROS C++ macro to tell SBPL to use ROS print statements
add_definitions(-DROS)

rosbuild_init()

rosbuild_add_boost_directories()

#find_package(Eigen REQUIRED)
#include_directories(${EIGEN_INCLUDE_DIRS})
#add_definitions(${EIGEN_DEFINITIONS})

#rosbuild_add_compile_flags(-g)

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

rosbuild_add_library(sbpl_manipulation_components_pr2
        src/sbpl_math.cpp
        src/orientation_solver.cpp 
        src/pr2_kdl_robot_model.cpp)

target_link_libraries(sbpl_manipulation_components_pr2 sbpl_manipulation_components)

