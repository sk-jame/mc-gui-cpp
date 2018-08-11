cmake_minimum_required(VERSION 3.0)
project(mc-gui)

###############################################################################
## file globbing ##############################################################
###############################################################################

# these instructions search the directory tree when cmake is
# invoked and put all files that match the pattern in the variables 
# `sources` and `data`
file(GLOB_RECURSE sources		*.cpp *.h)
# file(GLOB_RECURSE data			resources/*)
# you can use set(sources src/main.cpp) etc if you don't want to
# use globing to find files automatically

###############################################################################
## target definitions #########################################################
###############################################################################

# add the data to the target, so it becomes visible in some IDE
add_executable(mc-gui ${sources}) # ${data})

# just for example add some compiler flags
target_compile_options(mc-gui PUBLIC -std=c++17 -Wall -Wfloat-conversion)

# this lets me include files relative to the root src dir with a <> pair
target_include_directories(mc-gui PUBLIC ./)

# this copies all resource files in the build directory
# we need this, because we want to work with paths relative to the executable
# file(COPY ${data} DESTINATION resources)

###############################################################################
## dependencies ###############################################################
