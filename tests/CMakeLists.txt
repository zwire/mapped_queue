file(GLOB_RECURSE TESTS test_*.cpp)
foreach(test ${TESTS})
  get_filename_component(target ${test} NAME_WE)
  add_executable(${target} ${test})
  if(WIN32)
  else()
    target_link_libraries(${target} pthread)
  endif()
  add_test(NAME ${target} COMMAND ${target})
endforeach()
