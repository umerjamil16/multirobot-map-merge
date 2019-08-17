
# Multirobot map merging
I used [multirobot_map_merge](http://wiki.ros.org/multirobot_map_merge) package to merge maps from two robots simulated in [Stage](http://playerstage.sourceforge.net/doc/Stage-3.2.1/) robot simulator. 

![Visualization of Merged map](https://i.ibb.co/xYsfm3j/merged-map.png)

### Setting up the simulation environment

Move into ```~/catkin_ws/src``` directory and clone this repository in a folder called ```ca_mapping``` by running following command:

```git clone https://github.com/umerjamil16/multirobot-map-merge.git ca_mapping```
Now, run 

```roscore```

And source the ```.bash``` file.

```source ~/.bashrc```

```source ~/catkin_ws/devel/setup.bash```


### Using the multi_robot_map_merge package

 1. To launch Rviz,  ```.world``` file in Stage and broadcast respective TFs:

```roslaunch ca_mapping main.launch ```

 2. To launch ```gmapping``` node:

```roslaunch ca_mapping gmapping_3.launch```

 3. To launch ```multirobot_map_merge_package```:

```roslaunch ca_mapping map_merge.launch```

 4. To change the position of the robots, run the following command in a terminal:
```rosrun teleop_twist_keyboard teleop_twist_keyboard.py cmd_vel:=/robot_N/cmd_vel```

 5. Move into maps directory and save the merged map by:

``` rosrun map_server map_saver -f FILENAME map:=/map_merged_1```

 6. To provide the saved merged map:

```roslaunch ca_mapping provide_merged_map.launch```



### Other useful commands
To manually launch a ```.world``` file in Stage, move into world directory of this repository and run:.

```rosrun stage_ros stageros island.world ```

For TFs visualization:
```rosrun rqt_tf_tree rqt_tf_tree```

### ROS Packages used

 - [Stage_ros](http://wiki.ros.org/stage_ros)
 - [gmapping](http://wiki.ros.org/gmapping)
 - [multirobot_map_merge](http://wiki.ros.org/multirobot_map_merge)
