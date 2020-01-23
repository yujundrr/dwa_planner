# dwa_planner

## Enviornment
- Ubuntu 16.04 or 18.04
- ROS Kinetic or Melodic

## Install and Build

```
cd catkin_workspace/src
git clone https://github.com/amslabtech/dwa_planner.git
cd ..
catkin_make
```

## Nodes
### dwa_planner
- local planner node
#### Published topics
- /cmd_vel (geometry_msgs/Twist)
- ~/candidate_trajectoryies (visualization_msgs/MarkerArray)
  - for visualization
- ~/selected_trajectory (visualization_msgs/Marker)
  - for visualization

#### Subscribed topics
- /local_goal (geometry_msgs/PoseStamped)
  - the local goal must be in the local map
- /local_map (nav_msgs/OccupancyGrid)
  - robot-centered costmap
- /odom (nav_msgs/Odometry)
  - robot odometry

#### Parameters
- HZ
  - main loop rate (default: 20[Hz])
- TARGET_VELOCITY
  - max velocity of robot's target velocity (default: 0.8[m/s])
- ROBOT_FRAME
  - robot's coordinate frame (default: base_link)
  
#### Runtime requirement
- TF (from LocalMap_FRAME to ROBOT_FRAME) is required

## How to Use
- for local path planning
```
roslaunch dwa_planner local_planner.launch
```

## References
- D. Fox,  W. Burgard, and S.Thrun, "The dynamic window approach to collision avoidance", IEEE Robotics Automation Magazine, 1997.

(https://ieeexplore.ieee.org/abstract/document/580977)