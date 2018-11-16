project (PiFmRds)
cmake_minimum_required(VERSION 3.8)
SET(proj PiFmRds)

SET(CMAKE_CXX_STANDARD 11)
SET(CMAKE_CXX_EXTENSIONS OFF)
SET(CMAKE_CXX_STANDARD_REQUIRED ON)
SET(THREADS_PREFER_PTHREAD_FLAG ON)
SET(CMAKE_BUILD_FLAGS " -mfloat-abi=hard -pthread")
find_package(Threads REQUIRED)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -pedantic")

file(GLOB SOURCE_FILES
"*.h"
"*.cpp"
"*.c"
)


set(COMMON_INCLUDE_DIRS
        "/usr/local/include"
		"/usr/include"
        ${CMAKE_CURRENT_SOURCE_DIR}/external)

set(COMMON_LIBRARIES
		sndfile
		m
        dl
        pthread
        event
        Threads::Threads)

add_executable(${proj} ${SOURCE_FILES})
include_directories(${COMMON_INCLUDE_DIRS})
target_link_libraries(${proj} ${COMMON_LIBRARIES})