# Open vStorage VolumeDriver Buildtools

## Description

A collection of scripts and modifications to upstream sources to set the stage
for building VolumeDriver.

Currently two build flavours are supported: "release" and "rtchecked".
The former should be self explanatory, the latter is intended for development and
stands for "runtime checked" as the code is compiled without optimizations and
makes use of libstdc++'s debug mode (-D_GLIBCXX_DEBUG and -D_GLIBCXX_DEBUG_PEDANTIC).

## Prerequisites

The following tools and libraries (their development packages!) need to be available on the system:

* autotools (autoconf, automake, libtool)
* boost 1.57
* cmake
* doxygen
* g++ >= 4.9
* git
* lcov
* libc
* libc-ares
* libcurl
* librabbitmq
* openssl
* pylint
* make
* unzip
* wget

## Usage

(1) Create a config file that points to the desired install location and a path
    where downloaded artefacts will be stored, e.g.:

    $ cat ~/Projects/openvstorage/volumedriver-buildtools/rtchecked.config
    # PLACE WHERE THE BUILD WILL BE INSTALLED
    PREFIX=~/Projects/openvstorage/volumedriver-buildtools/rtchecked
    # PLACE WHERE THE SOURCES CAN BE FOUND
    SOURCES_DIR=~/Projects/openvstorage/volumedriver-buildtools/sources
    # number of parallel processes to use during the build phase -- default 2
    BUILD_NUM_PROCESSES=3

(2) Set the VOLUMEDRIVER_BUILD_CONFIGURATION env var to point to this config file
    and run build.sh of the desired flavour, e.g.:

    $ export VOLUMEDRIVER_BUILD_CONFIGURATION=~/Projects/openvstorage/volumedriver-buildtools/rtchecked.config
    $ cd src/rtchecked
    $ ./build.sh
