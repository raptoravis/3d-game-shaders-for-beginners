cmake_minimum_required(VERSION 3.11)


set(PROJECT_NAME "3d-game-shaders-for-beginners")
project(%{PROJECT_NAME})


set(SOURCES src/main.cxx src/unistd.h)

add_executable(${PROJECT_NAME} %{SOURCES})


target_include_directories(${PROJECT_NAME} $ENV{PANDA3D_ROOT}include)
target_link_directories(${PROJECT_NAME} $ENV{PANDA3D_ROOT}lib)

target_link_libraries(${PROJECT_NAME} libp3framework.lib libpanda.lib 
										libpandaexpress.lib libp3dtool.lib 
										libp3dtoolconfig.lib libp3direct.lib)

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_FILE:${PROJECT_NAME}> ${targetfile}
)