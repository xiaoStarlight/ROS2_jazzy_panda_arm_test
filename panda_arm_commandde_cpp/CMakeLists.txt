cmake_minimum_required(VERSION 3.8)
project(panda_arm_commandde_cpp)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(moveit_ros_planning_interface REQUIRED)
find_package(example_interfaces REQUIRED)
find_package(robot_arm_interfaces REQUIRED)

add_executable(commander src/commander_template.cpp)
ament_target_dependencies(commander rclcpp moveit_ros_planning_interface example_interfaces robot_arm_interfaces)

install(TARGETS
  commander
  DESTINATION lib/${PROJECT_NAME}/
)

ament_package()
