cmake_minimum_required(VERSION 3.0)
project(blake2 C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_FLAGS "-Wall -Wextra")
SET(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS} -g3 -rdynamic -export-dynamic -O0")
SET(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS} -O3 -march=native")

add_library(blake2s blake2s.c)
add_library(blake2b blake2b.c)

target_include_directories(blake2s PUBLIC ${PROJECT_SOURCE_DIR})
target_include_directories(blake2b PUBLIC ${PROJECT_SOURCE_DIR})

add_executable(selftest selftest.c)
target_link_libraries(selftest blake2s blake2b)
