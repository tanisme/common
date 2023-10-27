CMAKE_MINIMUM_REQUIRED(VERSION 3.26)

project(common)

SET(CMAKE_CXX_STANDARD 11)
SET(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
SET(CMAKE_DEBUG_POSTFIX "d")

#json
include_directories(src/jsoncpp/include)
add_library(jsoncpp STATIC
        src/jsoncpp/src/json_internalarray.inl
        src/jsoncpp/src/json_internalmap.inl
        src/jsoncpp/src/json_valueiterator.inl
        src/jsoncpp/src/json_reader.cpp
        src/jsoncpp/src/json_writer.cpp
        src/jsoncpp/src/json_value.cpp)


#sqlite
include_directories(sqlite3)
add_library(sqlite3 STATIC
        src/sqlite3/sqlite3.c
        src/sqlite3/sqliteimpl.cpp)

add_executable(main main.cpp)
target_link_libraries(main jsoncpp sqlite3)
