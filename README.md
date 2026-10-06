# so101_description

Description package for the SO-101 follower arm (https://github.com/TheRobotStudio/SO-ARM100) under ROS 2.

## Contents

- `urdf/so101_arm.xacro`: the `so101_arm` macro (`prefix`, `parent`, `*origin`)
- `urdf/so101.ros2_control.xacro`: `so101_arm_ros2_joints` (the joints alone, to put in a shared
  `<ros2_control>` block) and `so101_arm_ros2_control` (a standalone system)
- `urdf/so101.urdf.xacro`: the standalone arm, args `port` and `use_mock_hardware`
- `config/so101_controllers.yaml`: `joint_state_broadcaster`, `arm_controller`, `gripper_controller`

## How To Use

```bash
ros2 launch so101_description display.launch.py
ros2 launch so101_description hardware_control.launch.py use_mock_hardware:=true
```

`limp:=true` leaves the hardware inactive (torque never switched on) and starts only
`joint_state_broadcaster`, so you can move the arm by hand and watch the pose in RViz. See
`lekiwi_bringup/README.md`, "Limp mode", for the precautions.

## Attribution

The kinematics, inertials and meshes come from `Simulation/SO101/so101_new_calib.urdf` in
[TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100) (commit `5f6d2b8`),
generated with onshape-to-robot from the
[Onshape model](https://cad.onshape.com/documents/7715cc284bb430fe6dab4ffd/w/4fd0791b683777b02f8d975a/e/826c553ede3b7592eb9ca800).
They are used under the Apache License 2.0 (see `LICENSE`). Changes are listed in the header of
`urdf/so101_arm.xacro`.
