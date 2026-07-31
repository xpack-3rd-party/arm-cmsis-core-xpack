# -----------------------------------------------------------------------------
# DO NOT EDIT! Automatically generated from template file: xcdl-package.jsonc
#
# This file is part of the µOS++ project (https://micro-os-plus.github.io/).
# Copyright (c) 2021-2026 Liviu Ionescu. All rights reserved.
#
# Permission to use, copy, modify, and/or distribute this software for any
# purpose is hereby granted, under the terms of the MIT license.
#
# If a copy of the license was not distributed with this file, it can be
# obtained from https://opensource.org/licenses/mit.
#
# -----------------------------------------------------------------------------

# This file is intended to be used by applications via:
#
# `add_subdirectory("xpacks/@xpack-3rd-party/arm-cmsis-core")`
#
# This creates libraries that can be linked to a target with:
#
# ~~~
# target_link_libraries(your-target PUBLIC xpack-3rd-party::arm-cmsis-core-cortex-m)
# target_link_libraries(your-target PUBLIC xpack-3rd-party::arm-cmsis-core-cortex-a)
# target_link_libraries(your-target PUBLIC xpack-3rd-party::arm-cmsis-core)
# ~~~

# -----------------------------------------------------------------------------

# https://cmake.org/cmake/help/v3.20/
cmake_minimum_required (VERSION 3.20)
project (
  xpack-3rd-party-arm-cmsis-core
  DESCRIPTION "A source code library with Arm CMSIS Core"
  LANGUAGES C CXX ASM
)

# To access the optional functions, include the
# `cmake/micro-os-plus-build-helper.cmake` file from the
# `@micro-os-plus/build-helper` package.

if (COMMAND xpack_get_package_name_and_version)
  xpack_get_package_name_and_version (
    "${CMAKE_CURRENT_SOURCE_DIR}/package.json"
  )
  message (VERBOSE
           "Processing xPack ${PACKAGE_JSON_NAME}@${PACKAGE_JSON_VERSION}..."
  )
endif ()

# -----------------------------------------------------------------------------

# Interface libraries are the main targets, which consumers (like embedded
# applications) link against. It defines the public API and properties of the
# library; sources are propagated to and compiled by each consumer.

# They are aliased using namespaced syntax (Project::Target). This is the
# canonical pattern for consumption via target_link_libraries(), whether the
# dependency is added via add_subdirectory(), FetchContent, or an installed
# package via find_package(). Using "::" lets CMake detect an invalid or
# misspelled target name at configure time, rather than silently passing it
# through to the linker as a plain string or flag. Note: alias targets are
# read-only; properties must be set on the underlying target, not on the alias
# itself.

# https://cmake.org/cmake/help/v3.20/command/add_library.html?highlight=interface#interface-libraries
# Visibility keywords: PRIVATE applies to the target itself; INTERFACE passes
# properties up to targets that link against it; PUBLIC does both.
add_library (
  xpack-3rd-party-arm-cmsis-core-cortex-m-interface INTERFACE EXCLUDE_FROM_ALL
)

target_include_directories (
  xpack-3rd-party-arm-cmsis-core-cortex-m-interface
  INTERFACE "CMSIS/Core/Include"
)

target_compile_definitions (
  xpack-3rd-party-arm-cmsis-core-cortex-m-interface INTERFACE "__PROGRAM_START"
)

if (COMMAND xpack_display_target_lists)
  xpack_display_target_lists (xpack-3rd-party-arm-cmsis-core-cortex-m-interface)
endif ()

# -----------------------------------------------------------------------------
# Alias.

# https://cmake.org/cmake/help/v3.20/command/add_library.html#alias-libraries
add_library (
  xpack-3rd-party::arm-cmsis-core-cortex-m ALIAS
  xpack-3rd-party-arm-cmsis-core-cortex-m-interface
)
message (
  VERBOSE
  "> xpack-3rd-party::arm-cmsis-core-cortex-m -> xpack-3rd-party-arm-cmsis-core-cortex-m-interface"
)

# -----------------------------------------------------------------------------

# https://cmake.org/cmake/help/v3.20/command/add_library.html?highlight=interface#interface-libraries
# Visibility keywords: PRIVATE applies to the target itself; INTERFACE passes
# properties up to targets that link against it; PUBLIC does both.
add_library (
  xpack-3rd-party-arm-cmsis-core-cortex-a-interface INTERFACE EXCLUDE_FROM_ALL
)

target_include_directories (
  xpack-3rd-party-arm-cmsis-core-cortex-a-interface
  INTERFACE "CMSIS/Core_A/Include"
)

target_compile_definitions (
  xpack-3rd-party-arm-cmsis-core-cortex-a-interface INTERFACE "__PROGRAM_START"
)

if (COMMAND xpack_display_target_lists)
  xpack_display_target_lists (xpack-3rd-party-arm-cmsis-core-cortex-a-interface)
endif ()

# -----------------------------------------------------------------------------
# Alias.

# https://cmake.org/cmake/help/v3.20/command/add_library.html#alias-libraries
add_library (
  xpack-3rd-party::arm-cmsis-core-cortex-a ALIAS
  xpack-3rd-party-arm-cmsis-core-cortex-a-interface
)
message (
  VERBOSE
  "> xpack-3rd-party::arm-cmsis-core-cortex-a -> xpack-3rd-party-arm-cmsis-core-cortex-a-interface"
)

# -----------------------------------------------------------------------------

# https://cmake.org/cmake/help/v3.20/command/add_library.html?highlight=interface#interface-libraries
# Visibility keywords: PRIVATE applies to the target itself; INTERFACE passes
# properties up to targets that link against it; PUBLIC does both.
add_library (
  xpack-3rd-party-arm-cmsis-core-interface INTERFACE EXCLUDE_FROM_ALL
)

target_link_libraries (
  xpack-3rd-party-arm-cmsis-core-interface
  INTERFACE "xpack-3rd-party::arm-cmsis-core-cortex-m"
            "xpack-3rd-party::arm-cmsis-core-cortex-a"
)

if (COMMAND xpack_display_target_lists)
  xpack_display_target_lists (xpack-3rd-party-arm-cmsis-core-interface)
endif ()

# -----------------------------------------------------------------------------
# Alias.

# https://cmake.org/cmake/help/v3.20/command/add_library.html#alias-libraries
add_library (
  xpack-3rd-party::arm-cmsis-core ALIAS
  xpack-3rd-party-arm-cmsis-core-interface
)
message (
  VERBOSE
  "> xpack-3rd-party::arm-cmsis-core -> xpack-3rd-party-arm-cmsis-core-interface"
)

# -----------------------------------------------------------------------------
