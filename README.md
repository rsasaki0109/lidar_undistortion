lidar_undisrtoriton
====

header-only program of 3d lidar undistortion using 9-axis imu
separated from [LeGO-LOAM](https://github.com/RobustFieldAutonomyLab/LeGO-LOAM).  
It argues that the IMU center and the LIDAR center are aligned.
## how to use
Initialization
```cpp
#include <lidar_undistortion.hpp>

LidarUndistortion lidar_undistortion_;
double scan_period = ...; //The rotation period of lidar
lidar_undistortion_.setScanPeriod(scan_period);
```
when imu is received
```cpp
Eigen::Vector3f angular_velo{...};
Eigen::Vector3f acc{...};
Eigen::Quaternionf quat{...};
double imu_time = ...
lidar_undistortion_.getImu(angular_velo, acc, quat, imu_time);
```
when LIDAR scan is received
```cpp
// output:cloud_ptr
lidar_undistortion_.adjustDistortion(cloud_ptr, scan_time);
```

