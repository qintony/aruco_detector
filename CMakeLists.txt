cmake_minimum_required(VERSION 2.8.3)
project(tag_detector)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++11 -march=native -DEIGEN_DONT_PARALLELIZE")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall")

find_package(catkin REQUIRED COMPONENTS
    roscpp
    std_msgs
    cv_bridge 
    )
message(${catkin_INCLUDE_DIRS})
find_package(OpenCV REQUIRED)

find_package(Ceres 1.11.0 REQUIRED)
include_directories(${CERES_INCLUDE_DIRS})

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
find_package(Eigen3  REQUIRED)
include_directories(
  ${catkin_INCLUDE_DIRS}
  ${EIGEN3_INCLUDE_DIR}
)
message( "fuck!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!")
message(${catkin_INCLUDE_DIRS})
set(CMAKE_MODULE_PATH /usr/local/lib/cmake/)
find_package(aruco REQUIRED)


catkin_package(
    )

add_executable(tag_detector
    src/tag_detector_node.cpp)

target_link_libraries(tag_detector ${catkin_LIBRARIES} ${OpenCV_LIBS} ${aruco_LIBS} ${CERES_LIBRARIES})
