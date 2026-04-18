# ROS2_JuanMa — Puzzlebot Navigation Project

**TE3003B · Semestre Feb–Jun 2026**

Autonomous navigation project for the Puzzlebot (Jetson Lidar Edition) using ROS 2 Humble and Gazebo Classic. Includes SLAM-based mapping and Nav2-based autonomous navigation over a custom maze environment.

---

## Team members

| Name |
|------|
| Edgar Roann Santillan Bernal |
| Itzel Hernández Vargas |
| Jorge Martínez López |
| Santiago Reynaldo Aguilar Vega |

---

## Repository structure

puzzlebot_ros2/
├── puzzlebot_description/
├── puzzlebot_gazebo/
├── puzzlebot_navigation2/
└── README.md

---

## Prerequisites

| Tool | Version |
|------|---------|
| Ubuntu | 22.04 LTS |
| ROS 2 | Humble Hawksbill |
| Gazebo | Classic (gazebo_ros) |
| Python | 3.10 |
| slam_toolbox | humble |
| nav2_bringup | humble |

Install dependencies:

sudo apt install ros-humble-slam-toolbox ros-humble-nav2-bringup ros-humble-gazebo-ros-pkgs ros-humble-robot-state-publisher ros-humble-ros-gz-bridge

---

## Build & setup

git clone https://github.com/santidx123/ROS2_JuanMa.git
mkdir -p ~/puzzlebot_ws/src
cp -r ROS2_JuanMa/ ~/puzzlebot_ws/src/puzzlebot_ros2/
cd ~/puzzlebot_ws
colcon build
source install/setup.bash

---

## Launch — SLAM mode

ros2 launch puzzlebot_navigation2 slam.launch.xml

Move the robot:
ros2 run teleop_twist_keyboard teleop_twist_keyboard

Save the map:
ros2 run nav2_map_server map_saver_cli -f ~/map_maze

---

## Launch — Navigation mode

ros2 launch puzzlebot_navigation2 nav2.launch.xml

Use 2D Pose Estimate in RViz to set initial pose, then Nav2 Goal to send a destination.
