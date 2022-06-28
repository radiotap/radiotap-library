cmake_minimum_required(VERSION 3.11)
project(radiotap)

add_definitions("-D_DEFAULT_SOURCE -DRADIOTAP_SUPPORT_OVERRIDES")

add_library(radiotap STATIC radiotap.c)
set_target_properties(radiotap PROPERTIES
		      COMPILE_FLAGS "-Wall -Wextra -Wno-address-of-packed-member")

install(TARGETS radiotap DESTINATION lib)
install(FILES radiotap.h radiotap_iter.h DESTINATION include)

add_executable(parse parse.c)
set_target_properties(parse PROPERTIES
		      COMPILE_FLAGS "-Wall -Wextra")
target_link_libraries(parse radiotap)
