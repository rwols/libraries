string( CONCAT conditional_exclusion
  "$<NOT:$<AND:$<CXX_COMPILER_ID:MSVC>"
             ",$<VERSION_LESS:$<CXX_COMPILER_VERSION>,99>"
             ",$<BOOL:$<TARGET_PROPERTY:COROUTINES>"
               ">"
         ">"
   ">" )

target_sources( stlab INTERFACE
  $<BUILD_INTERFACE:
    $<${conditional_exclusion}:${CMAKE_CURRENT_SOURCE_DIR}/channel.hpp>
    ${CMAKE_CURRENT_SOURCE_DIR}/config.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/default_executor.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/executor_base.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/future.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/immediate_executor.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/main_executor.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/optional.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/progress.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/system_timer.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/task.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/traits.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/tuple_algorithm.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/utility.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/variant.hpp>
  $<INSTALL_INTERFACE:
    $<${conditional_exclusion}:include/stlab/concurrency/channel.hpp>
    include/stlab/concurrency/channel.hpp
    include/stlab/concurrency/config.hpp
    include/stlab/concurrency/default_executor.hpp
    include/stlab/concurrency/executor_base.hpp
    include/stlab/concurrency/future.hpp
    include/stlab/concurrency/immediate_executor.hpp
    include/stlab/concurrency/main_executor.hpp
    include/stlab/concurrency/optional.hpp
    include/stlab/concurrency/progress.hpp
    include/stlab/concurrency/system_timer.hpp
    include/stlab/concurrency/task.hpp
    include/stlab/concurrency/traits.hpp
    include/stlab/concurrency/tuple_algorithm.hpp
    include/stlab/concurrency/utility.hpp
    include/stlab/concurrency/variant.hpp> )
