cmake_minimum_required(VERSION 3.6)
project(RDMA)
enable_language(CXX)
enable_language(C)
enable_language(ASM)
set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_C_STANDARD 11)

set(CMAKE_CXX_FLAGS "-fpermissive ${CMAKE_CXX_FLAGS}")

include_directories(./)

add_executable(service src/service.cpp)

add_executable(double_service src/double_service.cpp)

add_executable(double_batch src/double_batch.cpp)

add_executable(service_batch src/service_batch.cpp)

target_link_libraries(service ibverbs pthread)
target_link_libraries(double_service ibverbs pthread)
target_link_libraries(service_batch ibverbs pthread)
target_link_libraries(double_batch ibverbs pthread)
