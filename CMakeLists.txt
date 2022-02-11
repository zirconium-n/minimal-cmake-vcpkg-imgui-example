cmake_minimum_required(VERSION 3.15)

set(VCPKG_DIR ../vcpkg)

# Setup vcpkg script with CMake (note: should be placed before project() call)
set(CMAKE_TOOLCHAIN_FILE ${VCPKG_DIR}/scripts/buildsystems/vcpkg.cmake CACHE STRING "Vcpkg toolchain file")
set(VCPKG_TARGET_TRIPLET "x86-windows")

project(Example)

set(CMAKE_CXX_STANDARD 20)
find_package(imgui REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
find_package(opengl REQUIRED)

add_executable(main src/main.cpp)
target_link_libraries(main PRIVATE imgui::imgui glfw opengl32)
