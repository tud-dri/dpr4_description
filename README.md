# dpr4_description
Unified Robot Description Format (URDF) of the DPR4 platform for the TU Delft Minor Robotics

Installation
================

Move to the src folder of you workspace
````
$ cd ~/<YOUR_WORKSPACE_PATH>/src/
````

Clone the repo into the src folder

````
$ git clone https://github.com/yappel/dpr4_description.git
````
Usage
===============
Create your own ros package for your robot (if you do not have one already)

````
$ catkin_create_pkg MY_ROBOT_description dpr4_description
````
In your package create an URDF xacro file where you import the dpr4 urdf and add your own components.
The file might look something like this:

````
<?xml version="1.0"?>
<robot name="MY_ROBOT" xmlns:xacro="http://ros.org/wiki/xacro">
   <xacro:include filename="$(find dpr4_description)/urdf/dpr4_description.urdf.xacro"/>

  <link name="example_link">
    <visual>
      <geometry>
        <cylinder length="0.6" radius="0.2"/>
      </geometry>
    </visual>
    <collision>
      <geometry>
        <cylinder length="0.6" radius="0.2"/>
      </geometry>
    </collision>
  </link>

  <joint name="example_link_to_base" type="fixed">
    <origin xyz="0 0 0" rpy="0 0 0" />
    <parent link="base_link" />
    <child link="example_link" />
  </joint>

</robot>

````
You now have an URDF ready to use. You can use this for multiple things, for example to view your robot in RVIZ as described [here] (http://wiki.ros.org/rviz/DisplayTypes/RobotModel)
