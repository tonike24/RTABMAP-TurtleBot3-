# RTABMAP-TurtleBot3-
En este proyecto embarca todo lo referido a la puesta en marcha, configuración y funcionalidad del algortimo RTABMAP en un TurtleBot3. Explicando todo lo necesario para entender el algortimo, las pruebas realizadas y los archivos a modificar para que funcione correctamente en nuestro TurtleBot3.

Es importante destacar que si se ha llamado algun archivo con un nombre distinto, el nombre para ejectuarlo será el correspondiente al nombre que tenga el archivo .launch

Abriendo la terminal (cntl + T) de Ubuntu se escribirán los siguientes comandos en el mismo orden:

- Comandos a ejecutar en el PC:

(1) roscore 

(2) ssh -X robotate@10.0.200.23 (Cambiar la IP por su correspondiente)

- Comandos a ejecutar utilizando la ventana remota del TurtleBot3

(3) roslaunch turtlebot3_bringup turtlebot3_astra.launch 

(4) rosrun nodelet nodelet load RTAB-MAP_ros/rgbd_sync camera/camera_nodelet_manager \__name:=rgbd_sync \camera/rgb/image:=/camera/rgb/image_rect_color \camera/depth/image:=/camera/depth_registered/image_raw \camera/rgb/camera_info:=/camera/rgb/camera_info

- Comandos a ejecutar en el PC:
    
(5) roslaunch turtlebot3_bringup turtlebot3_remote.

(6) roslaunch RTAB-MAP_ros rtabnavigation.launch subscribe_rgbd:=true rgbd_topic:=/camera/rgbd_image/compressed args:="-d""--delete_db_on_start" 

(7) roslaunch RTAB-MAP_ros rtabnavigation.launch subscribe_rgbd:=true rgbd_topic:=/camera/rgbd_image/compressed localization:=true rviz:=true RTAB-MAPviz:=false

(8) roslaunch RTAB-MAP_ros nav2.launch map_topic:=/map 

Comandos importantes durante la instalación de paquetes en ROS:

- sudo rosdep init

- rosdep update

- rosdep install AMAZING_PACKAGE

- rosdep install --from-paths ~/catkin_ws/src --ignore-src -r -y

- sudo apt-get update

- sudo apt-get dist-upgrade
