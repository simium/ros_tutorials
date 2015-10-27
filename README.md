# ros_tutorials
##Creating a ROS workspace
_Initialise the workspace_
```shell
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace
```

_Build an empty workspace_
```shell
$ cd ~/catkin_ws/
$ catkin_make
```

_Update your environment_
```shell
$ cd ~/catkin_ws/
$ source devel/setup.bash
```

##Navigating the ROS Filesystem
```shell
jp@ubuntu:~/catkin_ws$ rospack find roscpp
/opt/ros/indigo/share/roscpp

jp@ubuntu:~/catkin_ws$ roscd roscpp
jp@ubuntu:/opt/ros/indigo/share/roscpp$ pwd
/opt/ros/indigo/share/roscpp

jp@ubuntu:/opt/ros/indigo/share/roscpp$ roscd roscpp/cmake
jp@ubuntu:/opt/ros/indigo/share/roscpp/cmake$ pwd
/opt/ros/indigo/share/roscpp/cmake

jp@ubuntu:/opt/ros/indigo/share/roscpp/cmake$ roscd log
No active roscore

jp@ubuntu:~/.ros/log$ rosls roscpp_tutorials
cmake  launch  package.xml  srv
```
##Creating a ROS Package
```shell
$ cd ~/catkin_ws/src
$ catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
$ catkin_make
$ source ~/catkin_ws/devel/setup.bash
```

```shell
jp@ubuntu:~/catkin_ws$ rospack depends1 beginner_tutorials
roscpp
rospy
std_msgs

jp@ubuntu:~/catkin_ws$ roscd beginner_tutorials
jp@ubuntu:~/catkin_ws/src/beginner_tutorials$ cat package.xml
```
```xml
<?xml version="1.0"?>
<package>
  <name>beginner_tutorials</name>
  <version>0.0.0</version>
  <description>The beginner_tutorials package</description>

  <!-- One maintainer tag required, multiple allowed, one person per tag -->
  <!-- Example:  -->
  <!-- <maintainer email="jane.doe@example.com">Jane Doe</maintainer> -->
  <maintainer email="jp@todo.todo">jp</maintainer>


  <!-- One license tag required, multiple allowed, one license per tag -->
  <!-- Commonly used license strings: -->
  <!--   BSD, MIT, Boost Software License, GPLv2, GPLv3, LGPLv2.1, LGPLv3 -->
  <license>TODO</license>


  <!-- Url tags are optional, but mutiple are allowed, one per tag -->
  <!-- Optional attribute type can be: website, bugtracker, or repository -->
  <!-- Example: -->
  <!-- <url type="website">http://wiki.ros.org/beginner_tutorials</url> -->


  <!-- Author tags are optional, mutiple are allowed, one per tag -->
  <!-- Authors do not have to be maintianers, but could be -->
  <!-- Example: -->
  <!-- <author email="jane.doe@example.com">Jane Doe</author> -->


  <!-- The *_depend tags are used to specify dependencies -->
  <!-- Dependencies can be catkin packages or system dependencies -->
  <!-- Examples: -->
  <!-- Use build_depend for packages you need at compile time: -->
  <!--   <build_depend>message_generation</build_depend> -->
  <!-- Use buildtool_depend for build tool packages: -->
  <!--   <buildtool_depend>catkin</buildtool_depend> -->
  <!-- Use run_depend for packages you need at runtime: -->
  <!--   <run_depend>message_runtime</run_depend> -->
  <!-- Use test_depend for packages you need only for testing: -->
  <!--   <test_depend>gtest</test_depend> -->
  <buildtool_depend>catkin</buildtool_depend>
  <build_depend>roscpp</build_depend>
  <build_depend>rospy</build_depend>
  <build_depend>std_msgs</build_depend>
  <run_depend>roscpp</run_depend>
  <run_depend>rospy</run_depend>
  <run_depend>std_msgs</run_depend>


  <!-- The export tag contains other, unspecified, tags -->
  <export>
    <!-- Other tools can request additional information be placed here -->

  </export>
```

_Let's clean the final package.xml_
```xml
<?xml version="1.0"?>
<package>
  <name>beginner_tutorials</name>
  <version>0.1.0</version>
  <description>The beginner_tutorials package for UVic Master on Robotics</description>

  <maintainer email="do.not.want.spam@uvic.cat">Juampe</maintainer>
  <license>BSD</license>
  <url type="repository">http://github.com/simium</url>
  <author email="do.not.want.spam@uvic.cat">Juampe</maintainer>


  <buildtool_depend>catkin</buildtool_depend>

  <build_depend>roscpp</build_depend>
  <build_depend>rospy</build_depend>
  <build_depend>std_msgs</build_depend>

  <run_depend>roscpp</run_depend>
  <run_depend>rospy</run_depend>
  <run_depend>std_msgs</run_depend>

</package>
```

##Building a ROS Package
```shell
jp@ubuntu:~/catkin_ws/src$ ls
beginner_tutorials  CMakeLists.txt

jp@ubuntu:~/catkin_ws/src$ cd ..
jp@ubuntu:~/catkin_ws$ ls
build  devel  src

jp@ubuntu:~/catkin_ws$ catkin_make
Base path: /home/jp/catkin_ws
Source space: /home/jp/catkin_ws/src
Build space: /home/jp/catkin_ws/build
Devel space: /home/jp/catkin_ws/devel
Install space: /home/jp/catkin_ws/install
Invalid package manifest "/home/jp/catkin_ws/src/beginner_tutorials/package.xml": The manifest contains invalid XML:
mismatched tag: line 10, column 52
jp@ubuntu:~/catkin_ws$ catkin_make
Base path: /home/jp/catkin_ws
Source space: /home/jp/catkin_ws/src
Build space: /home/jp/catkin_ws/build
Devel space: /home/jp/catkin_ws/devel
Install space: /home/jp/catkin_ws/install
####
#### Running command: "make cmake_check_build_system" in "/home/jp/catkin_ws/build"
####
-- Using CATKIN_DEVEL_PREFIX: /home/jp/catkin_ws/devel
-- Using CMAKE_PREFIX_PATH: /home/jp/catkin_ws/devel;/opt/ros/indigo
-- This workspace overlays: /home/jp/catkin_ws/devel;/opt/ros/indigo
-- Using PYTHON_EXECUTABLE: /usr/bin/python
-- Using Debian Python package layout
-- Using empy: /usr/bin/empy
-- Using CATKIN_ENABLE_TESTING: ON
-- Call enable_testing()
-- Using CATKIN_TEST_RESULTS_DIR: /home/jp/catkin_ws/build/test_results
-- Found gtest sources under '/usr/src/gtest': gtests will be built
-- Using Python nosetests: /usr/bin/nosetests-2.7
-- catkin 0.6.14
-- BUILD_SHARED_LIBS is on
-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
-- ~~  traversing 1 packages in topological order:
-- ~~  - beginner_tutorials
-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
-- +++ processing catkin package: 'beginner_tutorials'
-- ==> add_subdirectory(beginner_tutorials)
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jp/catkin_ws/build
####
#### Running command: "make -j4 -l4" in "/home/jp/catkin_ws/build"
####

jp@ubuntu:~/catkin_ws$ ls
build  devel  src
```

##Understanding ROS Nodes
We are going to need more than one terminal to run the commands below.

```shell
[SHELL 1] jp@ubuntu:~/catkin_ws$ roscore
... logging to /home/jp/.ros/log/0e33b6a0-7c95-11e5-b394-b888e3e04b40/roslaunch-Circutor-19795.log
Checking log directory for disk usage. This may take awhile.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://localhost:34201/
ros_comm version 1.11.13


SUMMARY
========

PARAMETERS
 * /rosdistro: indigo
 * /rosversion: 1.11.13

NODES

auto-starting new master
process[master]: started with pid [19807]
ROS_MASTER_URI=http://localhost:11311/

setting /run_id to 0e33b6a0-7c95-11e5-b394-b888e3e04b40
process[rosout-1]: started with pid [19820]
started core service [/rosout]


[SHELL 2] jp@ubuntu:~/catkin_ws$ rosnode list
/rosout
[SHELL 2] jp@ubuntu:~/catkin_ws$ rosnode info /rosout
--------------------------------------------------------------------------------
Node [/rosout]
Publications:
 * /rosout_agg [rosgraph_msgs/Log]

Subscriptions:
 * /rosout [unknown type]

Services:
 * /rosout/set_logger_level
 * /rosout/get_loggers


contacting node http://localhost:37525/ ...
Pid: 19820

[SHELL 2] jp@ubuntu:~/catkin_ws$ rosrun turtlesim turtlesim_node
[ INFO] [1445941610.752629135]: Starting turtlesim with node name /turtlesim
[ INFO] [1445941610.765313710]: Spawning turtle [turtle1] at x=[5,544445], y=[5,544445], theta=[0,000000]
```
![alt text](http://i.imgur.com/UUOC9V7.png "My turtle simulator.")

```shell
[SHELL 3] jp@ubuntu:~/catkin_ws$ rosnode list
/rosout
/turtlesim

[SHELL 3] jp@ubuntu:~/catkin_ws$ rosrun turtlesim turtlesim_node __name:=my_robo_turtle
[ INFO] [1445942039.856948041]: Starting turtlesim with node name /my_robo_turtle
[ INFO] [1445942039.866167813]: Spawning turtle [turtle1] at x=[5,544445], y=[5,544445], theta=[0,000000]

[SHELL 4] jp@ubuntu:~/catkin_ws$ rosnode list
/my_robo_turtle
/rosout
/turtlesim

[SHELL 4] jp@ubuntu:~/catkin_ws$ rosnode ping my_robo_turtle
rosnode: node is [/my_robo_turtle]
pinging /my_robo_turtle with a timeout of 3.0s
xmlrpc reply from http://localhost:51156/	time=0.732899ms
xmlrpc reply from http://localhost:51156/	time=1.176834ms
xmlrpc reply from http://localhost:51156/	time=1.235008ms
xmlrpc reply from http://localhost:51156/	time=1.034021ms
^Cping average: 1.044691ms
```

![alt text](http://i.imgur.com/afYKFvH.png "Another turtle simulator.")

##Understanding ROS Topics
```shell
[SHELL 5] jp@ubuntu:~/catkin_ws$ rosrun turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
```

![alt text](http://i.imgur.com/oIIczsx.png "Our turtle simulator after some movement.")

```shell
[SHELL 4] jp@ubuntu:~/catkin_ws$ rosrun rqt_graph rqt_graph
```

![alt text](http://i.imgur.com/IcUwgbj.png "Our turtle simulator represented as a graph.")

```shell
jp@ubuntu:~/catkin_ws$ rostopic echo /turtle1/cmd_vel
linear:
  x: 2.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0
---
linear:
  x: 0.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 2.0
---
linear:
  x: 2.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0
---
linear:
  x: 0.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 2.0
---
```

![alt text](http://i.imgur.com/uZtEV8i.png "Our turtle simulator represented as a graph.")

```shell
[SHELL 6] jp@ubuntu:~/catkin_ws$ rostopic list -v

Published topics:
 * /turtle1/color_sensor [turtlesim/Color] 2 publishers
 * /turtle1/cmd_vel [geometry_msgs/Twist] 1 publisher
 * /rosout [rosgraph_msgs/Log] 4 publishers
 * /rosout_agg [rosgraph_msgs/Log] 1 publisher
 * /turtle1/pose [turtlesim/Pose] 2 publishers

Subscribed topics:
 * /turtle1/cmd_vel [geometry_msgs/Twist] 2 subscribers
 * /rosout [rosgraph_msgs/Log] 1 subscriber
 * /statistics [rosgraph_msgs/TopicStatistics] 1 subscriber

[SHELL 6] jp@ubuntu:~/catkin_ws$ rostopic type /turtle1/cmd_vel
geometry_msgs/Twist

[SHELL 6] jp@ubuntu:~/catkin_ws$ rosmsg show geometry_msgs/Twist
geometry_msgs/Vector3 linear
  float64 x
  float64 y
  float64 z
geometry_msgs/Vector3 angular
  float64 x
  float64 y
  float64 z


jp@ubuntu:~/catkin_ws$ rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'
publishing and latching message for 3.0 seconds
```

![alt text](http://i.imgur.com/mK8nrmK.png "Our turtle simulator after rostopic transformation.")


```shell
[SHELL 6] jp@ubuntu:~/catkin_ws$ rostopic pub /turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, -1.8]'

[SHELL 7] jp@ubuntu:~/catkin_ws$ rosrun rqt_plot rqt_plot
```

![alt text](http://i.imgur.com/IEij09E.png "Our turtle simulator after rostopic transformation.")

![alt text](http://i.imgur.com/RTQJ20A.png "Our turtle simulator after rostopic transformation.")

![alt text](http://i.imgur.com/A2gW2Kq.png "Our turtle simulator represented in rqt_plot.")

##Understanding ROS Services and Parameters
```shell
jp@ubuntu:~/catkin_ws$ rosservice list
/clear
/kill
/my_robo_turtle/get_loggers
/my_robo_turtle/set_logger_level
/reset
/rosout/get_loggers
/rosout/set_logger_level
/spawn
/teleop_turtle/get_loggers
/teleop_turtle/set_logger_level
/turtle1/set_pen
/turtle1/teleport_absolute
/turtle1/teleport_relative
/turtlesim/get_loggers
/turtlesim/set_logger_level

jp@ubuntu:~/catkin_ws$ rosservice call /clear

jp@ubuntu:~/catkin_ws$ rosservice type spawn | rossrv show
float32 x
float32 y
float32 theta
string name
---
string name

jp@ubuntu:~/catkin_ws$ rosservice call spawn 2 2 0.2 ""
name: turtle2

```

![alt text](http://i.imgur.com/olrTD6c.png "New turtle simulator.")
![alt text](http://i.imgur.com/xZTQFkT.png "New turtle simulator after clear.")
![alt text](http://i.imgur.com/Ru9atgm.png "New turtle simulator after clear and a new turtle spawn.")

```shell
jp@ubuntu:~/catkin_ws$ rosparam list
/background_b
/background_g
/background_r
/rosdistro
/roslaunch/uris/host_localhost__34201
/rosversion
/run_id

jp@ubuntu:~/catkin_ws$ rosparam set /background_r 150
jp@ubuntu:~/catkin_ws$ rosparam get /background_r
150

jp@ubuntu:~/catkin_ws$ rosservice call clear
```

![alt text](http://i.imgur.com/RMMdyXF.png "Background color -red channel- changed.")

```shell
jp@ubuntu:~/catkin_ws$ rosparam dump params.yaml
jp@ubuntu:~/catkin_ws$ rosparam load params.yaml my_params
jp@ubuntu:~/catkin_ws$ rosparam get my_params/background_b
255
```

##Using rqt_console and roslaunch
###rqt_console
```shell
[SHELL 1] jp@ubuntu:~/catkin_ws$ roscore
[SHELL 2] jp@ubuntu:~/catkin_ws$ rosrun rqt_console rqt_console
[SHELL 3] jp@ubuntu:~/catkin_ws$ rosrun rqt_logger_level rqt_logger_level
[SHELL 4] jp@ubuntu:~/catkin_ws$ rosrun turtlesim turtlesim_node __name:=my_robo_turtle
```

![alt text](http://i.imgur.com/g20mc5U.png "Run a new turtle.")

![alt text](http://i.imgur.com/vxZbODY.png "ROS console.")

###roslaunch

```shell
[SHELL 1] jp@ubuntu:~/catkin_ws$ source devel/setup.bash
[SHELL 1] jp@ubuntu:~/catkin_ws$ roscd beginner_tutorials
[SHELL 1] jp@ubuntu:~/catkin_ws/src/beginner_tutorials$ mkdir launch
[SHELL 1] jp@ubuntu:~/catkin_ws/src/beginner_tutorials$ cd launch
[SHELL 1] jp@ubuntu:~/catkin_ws/src/beginner_tutorials/launch$ vim turtlemimic.launch
[SHELL 1] jp@ubuntu:~/catkin_ws/src/beginner_tutorials/launch$ roslaunch beginner_tutorials turtlemimic.launch
... logging to /home/jplopez/.ros/log/b0c37846-7ca0-11e5-8ca2-b888e3e04b40/roslaunch-Circutor-22745.log
Checking log directory for disk usage. This may take awhile.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://localhost:46697/

SUMMARY
========

PARAMETERS
 * /rosdistro: indigo
 * /rosversion: 1.11.13

NODES
  /
    mimic (turtlesim/mimic)
  /turtlesim1/
    sim (turtlesim/turtlesim_node)
  /turtlesim2/
    sim (turtlesim/turtlesim_node)

ROS_MASTER_URI=http://localhost:11311

core service [/rosout] found
process[turtlesim1/sim-1]: started with pid [22763]
process[turtlesim2/sim-2]: started with pid [22764]
process[mimic-3]: started with pid [22767]


[SHELL 2] jp@ubuntu:~/catkin_ws$ rostopic pub /turtlesim1/turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, -1.8]'

[SHELL 3] jp@ubuntu:~/catkin_ws$ rqt_graph

```

![alt text](http://i.imgur.com/4NwpKL4.png "Run a new turtle.")

![alt text](http://i.imgur.com/07eJvM5.png "ROS graph.")

##Using rosed
Currently my editor is vim, which is the default for rosed.

```shell
jp@ubuntu:~/catkin_ws$ rosed roscpp[TAB TAB]
roscpp                roscpp_serialization  roscpp_traits         roscpp_tutorials
jp@ubuntu:~/catkin_ws$ rosed roscpp [TAB TAB]
Empty.srv                   GetLoggers.srv              package.xml                 roscppConfig-version.cmake  SetLoggerLevel.srv
genmsg_cpp.py               Logger.msg                  roscpp.cmake                roscpp-msg-extras.cmake
gensrv_cpp.py               msg_gen.py                  roscppConfig.cmake          roscpp-msg-paths.cmake

##Examining Publisher and Subscriber
[SHELL 1] jp@ubuntu:~/catkin_ws$ roscore

[SHELL 2] jp@ubuntu:~/catkin_ws$ rosrun beginner_tutorials talker
[ INFO] [1445950333.389467084]: hello world 0
[ INFO] [1445950333.489584854]: hello world 1
[ INFO] [1445950333.589480121]: hello world 2
[ INFO] [1445950333.689464989]: hello world 3
[ INFO] [1445950333.789467550]: hello world 4
[ INFO] [1445950333.889471761]: hello world 5
[ INFO] [1445950333.989479583]: hello world 6
[ INFO] [1445950334.089482532]: hello world 7
[ INFO] [1445950334.189464332]: hello world 8
[ INFO] [1445950334.289475509]: hello world 9
[ INFO] [1445950334.389484892]: hello world 10
[ INFO] [1445950334.489461049]: hello world 11
[ INFO] [1445950334.589470126]: hello world 12
[ INFO] [1445950334.689497845]: hello world 13
[ INFO] [1445950334.789475380]: hello world 14
^C[ INFO] [1445950334.889599193]: hello world 15

[SHELL 3] jp@ubuntu:~/catkin_ws$ rosrun beginner_tutorials listener
[ INFO] [1445950333.689916367]: I heard: [hello world 3]
[ INFO] [1445950333.789868482]: I heard: [hello world 4]
[ INFO] [1445950333.889953701]: I heard: [hello world 5]
[ INFO] [1445950333.989922282]: I heard: [hello world 6]
[ INFO] [1445950334.089914866]: I heard: [hello world 7]
[ INFO] [1445950334.189858154]: I heard: [hello world 8]
[ INFO] [1445950334.289882219]: I heard: [hello world 9]
[ INFO] [1445950334.389887341]: I heard: [hello world 10]
[ INFO] [1445950334.489874518]: I heard: [hello world 11]
[ INFO] [1445950334.589825468]: I heard: [hello world 12]
[ INFO] [1445950334.689898806]: I heard: [hello world 13]
[ INFO] [1445950334.789826078]: I heard: [hello world 14]

```
