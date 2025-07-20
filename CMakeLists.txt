cmake_minimum_required(VERSION 3.10)
project(log_system)

# 设置C++标准
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 编译选项
add_compile_options( -Wall -O2)
# 查找pthread库
find_package(Threads REQUIRED)
find_package(jsoncpp REQUIRED)

# 设置目录
set(SRC_DIR ${CMAKE_SOURCE_DIR}/src/logs_code)
set(TEST_DIR ${CMAKE_SOURCE_DIR}/examples)

# 源文件
file(GLOB SOURCES "${SRC_DIR}/*.cpp")
# 添加头文件目录
include_directories(${SRC_DIR})

# 创建测试可执行文件
add_executable(test 
    ${SOURCES}
    ${TEST_DIR}/test.cpp
)

# 链接pthread库
target_link_libraries(test PRIVATE Threads::Threads)
target_link_libraries(test PRIVATE jsoncpp)
