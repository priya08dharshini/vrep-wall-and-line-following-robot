# vrep-wall-and-line-following-robot


Coppeliasim software and environmental setup:

CoppeliaSim Edu (previously known as V-REP) is a robot simulator with integrated development environment and is based on a distributed control architecture:
each object/model can be individually controlled via an embedded script, a plugin, a ROS or BlueZero node, a remote API client, or a custom solution,
which makes CoppeliaSim very versatile and ideal for multi-robot applications. 
Controllers can be written in C/C++, Python, Java, Lua, Matlab or Octave (coppeliarobotics.com, online).
We are interested in the python controller especially for our work.

CONCEPT OF LINE FOLLOWER:

The concept of working of line follower is related to light. We use here the behaviour of light at the black and white surfaces. 
When light falls on a white surface it is almost fully reflected and in the case of a black surface light is completely absorbed. 
This behaviour of light is used in building a line follower robot. In this Arduino based line follower robot, we have used IR Transmitters and IR receivers 
also called photodiodes. They are used for sending and receiving light. IR transmits infrared lights. When infrared rays fall on the white surface, 
it’s reflected back and caught by photodiodes which generate some voltage changes. When IR light falls on a black surface, light is absorbed by the black surface 
and no rays are reflected back, thus photo diode does not receive any light or rays. Here in this Arduino line follower robot when the sensor senses white surface
then Arduino gets 1 as input and when senses black line Arduino gets 0 as input. Building a Line follower robot using Arduino is interesting. 
The line follower robot senses a black line by using a sensor and then sends the signal to Arduino. Then Arduino drives the motor according to sensors' output.
Here in this project, we are using two IR sensor modules namely the left sensor and the right sensor. When both left and right sensor senses white then the robot moves forward.
If the left sensor comes on a black line then the robot turn the left side. If the right sensor sense black line then robot turn right side until both sensors comes at the
white surface. When the white surface comes robot starts moving on forward again. If both sensors come on the black line, the robot stops.

![Screenshot (116)](https://user-images.githubusercontent.com/81368192/149876175-4d7808cd-beee-4c9f-bf61-bfae302b64e1.png)


 WALL FOLLOWER:
In order to follow walls, you need at least two sensors (2 bits of information) to handle the four potential situations the robot could be in. 
One sensor has to be in the front, and the second could be on the left or right of the robot. The more sensors you use, the more information you have, so you can make
better judgements about what is going on. For this example, I just used two. The robot cannot find the wall, so you have to place the robot next to the wall. 
If you placed it in the middle of the room, it would just drive in circles. In order to work, I had to add code to turn hard left. Hard left just means I only turn on 
the right wheel so the robot basically turns in place rather than continue to move forward while turning. I couldn't just turn slowly like line follower because you have
no idea how close the robot is to the wall. This is a limitation of the sensor I chose, because the sensor reflects differently based on the surface. Additionally,
the logic is set up to only be binary because there is no way to tell the distance based on the sensor. If you knew distance, you could add additional logic to vary the
speed based on the distance to make the robot travel around the room faster. I actually couldn't get the sensor to reflect at all off a black surface, 
so in the video you'll see I had to put a white surface in front of the dishwasher. An audio based sensor would not have this problem.

![Screenshot (117)](https://user-images.githubusercontent.com/81368192/149876357-3dfa4c9e-b776-4a15-8e23-4623984ca1b1.png)


ENVIRONMENTAL SETUP FOR LINE FOLLOWING AND WALL FOLLOWING:

![Screenshot (118)](https://user-images.githubusercontent.com/81368192/149876788-d4c935a1-aa2d-4026-87bc-ca5a50d2e2a7.png)

Making a path in v-rep software is quite easy. A path is a pseudo object, representing a succession of points with orientation in space. pseudo object, since it is built using merely dummies and a customization script that describes its functionality and behaviour. Path objects can be added to the scene Â with [Menu bar --> Add --> Path].
A path is composed by control points that define its curve in space. Control points can be shifted, copy/pasted or deleted.

![Screenshot (119)](https://user-images.githubusercontent.com/81368192/149876801-20453aa7-f9aa-422d-8ba4-b8a410354dd5.png)

1.	The map compromises a wall which is the skeleton of the path to follow
2.	 It contains lines that indicate the ideal path that the robot should follow and 
3.	 A bounding box around the area so the robot cannot escape.
It compromises a square plane surrounded by a 15 meters bounding box, with addition of a 2 by 2 meter smaller box placed inside the surrounding walls in the 
far right corner, and a further 8 by 4 meter walls. The task was completed successfully, a program was developed that starts at a random position on the scene presented above, takes a random turn, and follows the walls on a determined path. 

RESULTS: 

![Screenshot (120)](https://user-images.githubusercontent.com/81368192/149877252-723b24cc-005b-405d-a408-c45f087d607d.png)
![Screenshot (121)](https://user-images.githubusercontent.com/81368192/149877264-ea7c1deb-c307-4937-888f-94ec47c74854.png)




 


