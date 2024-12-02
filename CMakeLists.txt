cmake_minimum_required(VERSION 3.10)

# 设置项目名称和版本
project(HelloWorld VERSION 1.0)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
# 启用 FetchContent 模块
include(FetchContent)

# 下载并构建 fmt 库
FetchContent_Declare(
  fmt
  GIT_REPOSITORY https://github.com/fmtlib/fmt.git
  GIT_TAG        master  # 或者指定具体版本如 "9.1.0"
)

# FetchContent_MakeAvailable 会自动下载并编译 fmt 库
FetchContent_MakeAvailable(fmt)

# 添加可执行文件
add_executable(hello main.cpp)

# 链接 fmt 库
target_link_libraries(hello PRIVATE fmt::fmt)
