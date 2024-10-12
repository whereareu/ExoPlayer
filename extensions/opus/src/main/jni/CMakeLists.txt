# Minimum CMake version required
cmake_minimum_required(VERSION 3.4.1)

# Set the path to the Opus include directory and source directory
set(OPUS_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/opus/include)
set(OPUS_SOURCE_DIR ${CMAKE_SOURCE_DIR}/opus/src)

# Add the Opus source files (.c files)
file(GLOB OPUS_SOURCES ${OPUS_SOURCE_DIR}/*.c)

# Add the Opus library as a shared library
add_library(opus SHARED ${OPUS_SOURCES})

# Include the Opus headers
include_directories(${OPUS_INCLUDE_DIR})

# Add the JNI interface for Opus
add_library(opus_jni SHARED opus_jni.cc)

# Link the opus_jni library with the compiled opus library
target_link_libraries(opus_jni opus)

