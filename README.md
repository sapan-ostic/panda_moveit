A **Gazebo simulator** for the Franka Emika Panda robot with ROS interface, providing exposed **controllers** and real-time **robot state feedback** similar to the real robot when using the [*franka-ros*][franka-ros] package.

### Installation

ROS Kinetic

#### Dependencies

- *libfranka* (`apt install ros-kinetic-libfranka` or [install from source][libfranka-doc])
- *franka-ros* v0.6.0 ([install from source][libfranka-doc]). *Make sure to use the [v0.6.0 release version](https://github.com/frankaemika/franka_ros/commit/49e5ac1055e332581b4520a1bd9ac8aaf4580fb1) if building from source. (`git checkout 49e5ac1` from the cloned franka_ros github repo.)*

For other possible missing dependencies, check the `apt` packages specified in Dockerfile.

The following dependencies can be installed using the `.rosinstall` file (instructions in next section)

- [*Franka ROS Interface*][fri-repo]
- [*franka_panda_description*][fpd-repo] (urdf and model files from *panda_description* package modified to work in Gazebo, and with the custom controllers)
- [*orocos-kinematics-dynamics*](https://github.com/orocos/orocos_kinematics_dynamics)

#### Building the Package

1.Clone the repo:

```bash
    cd <catkin_ws>/src
    git clone https://github.com/sapan-ostic/panda_moveit
```
2. Run 
```
cd panda_moveit
pip install -r requirements.txt
```
3. Build by running `./build_ws.sh` from `<catkin_ws>/src/panda_moveit`.

### Usage
The simulator can be started by running:

```bash
    roslaunch panda_gazebo panda_world.launch # (use argument load_gripper:=false for starting without gripper; see other available arguments in launch file)
```

To start without moveit server, add the argument `start_moveit:=false` to the command. This is sometimes necessary for starting nodes in the right order

- Run `roslaunch panda_simulator_examples demo_moveit.launch` to run a demo for testing the moveit planner interface with the simulated robot. This script starts a moveit RViz GUI for motion planning and terminal interface for modifying planning scene.
