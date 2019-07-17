# Minimum version of CMake required is 2.6
cmake_minimum_required(VERSION 2.6)

# Name of the top-level project / solution
#  is LearnBoostAsio
project("boost")

include_directories(
        D:\\program\\boost_1_70_0
        .\\common
)

link_directories(
        D:\\program\\boost_1_70_0\\lib64-msvc-14.1
)

# Glob all .cpp files
#file(GLOB CPP_SRCS *.cpp)
file(GLOB_RECURSE CPP_SRCS ${CMAKE_SOURCE_DIR}/*.cpp)
#list(APPEND CPP_SRCS ${CMAKE_SOURCE_DIR}/csrc/thirdparty/whereami/whereami.c)
#file(GLOB_RECURSE CPP_SRCS ${CMAKE_SOURCE_DIR}/functional/*.cpp)
#file(GLOB CPP_SRCS functional\\*.cpp)

foreach (cpp_file IN LISTS CPP_SRCS)
    #get_filename_component (exe_name ${cpp_file} NAME_WE)
    get_filename_component (exe_name1 ${cpp_file} ABSOLUTE)
	string(REPLACE "D:/cpp_boost_profesional/" "" exe_name2 ${exe_name1})
	string(REPLACE "/" "_" exe_name3 ${exe_name2})
	string(REPLACE ".cpp" "" exe_name ${exe_name3})
    # Create an executable
    add_executable(${exe_name} ${cpp_file})

    if (UNIX)
        # Link the libraries Foo and Bar to the executable.
        # Shared libraries preferred over static libraries when both present.
        # Libraries looked up in directories specified using link_directories.
        # target_link_libraries(${exe_name} ${Boost_SYSTEM_LIBRARY})
    endif()
endforeach()