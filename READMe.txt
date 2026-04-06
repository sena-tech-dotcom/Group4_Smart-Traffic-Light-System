Slide 1:


SMART TRAFFIC LIGHT SYSTEM
MICROPROCESSORS PROJECT 1
GROUP 4
GROUP MEMBERS: 
ABOVE STEPHEN KOI			7341123
AGBOWADA WISDOM SENA			7341523
ODURO AGNES				7343823
ANOKYE EUGENE DONKOR			7342223
MENSAH SOLOMON KWAKU			7343523
KOBZIE FUZIEMATA				7343323



Slide 2:
Table of contents:
Problem Statement………………………………………………………….3
Methodology………………………………………………………………..5
Simulation…………………………………………………………………..15
Conclusion…………………………………………………………………..16


Slide 3:
Problem statement:
Modern urban intersections often rely on fixed-time traffic light systems, which allocate equal signal durations to all roads regardless of actual traffic conditions. This leads to several inefficiencies, including:
Unnecessary delays on roads with little or no traffic 
Increased congestion on heavily populated roads 
Wasted fuel and higher emissions due to prolonged waiting times 
Driver frustration and reduced overall traffic efficiency 
In many developing regions and growing cities, traffic density is not uniform across all directions, and it varies significantly throughout the day. Traditional systems fail to adapt to these dynamic conditions.

Slide 4:
Problem statement:
Therefore, there is a need for an intelligent and adaptive traffic control system that can:
Monitor real-time traffic conditions 
Dynamically allocate green light durations 
Prioritize roads with higher vehicle density 
Minimize waiting time and improve traffic flow efficiency 
This project proposes the design and implementation of a Smart Traffic Light System using ultrasonic sensors, a microcontroller (ESP32), and visual display units (LED traffic lights, 7-segment display, and LCD). The system measures vehicle proximity on two intersecting roads and adjusts signal timing accordingly, ensuring optimal traffic management at a two-way intersection.


Slide 5:
METHODOLOGY:
1. System Design Approach
To address the inefficiencies of fixed-time traffic systems, an adaptive traffic control approach was adopted. The system dynamically adjusts traffic light durations based on real-time vehicle presence using ultrasonic sensors.
The methodology involves three main stages:
Sensing (Data Acquisition) 
Decision Making (Processing & Logic) 
Actuation (Traffic Control Output) 
This ensures that traffic signals respond intelligently to varying traffic conditions at a two-way intersection (Road A and Road B).


Slide 6:
METHODOLOGY:
2. Hardware Architecture
The system is built around a microcontroller (ESP32) which interfaces with the following components:
2.1 Ultrasonic Sensors 
Two sensors are used: 
Sensor A → monitors Road A 
Sensor B → monitors Road B 
Each sensor measures the distance of vehicles from the intersection. 
Shorter distance indicates higher traffic density.


Slide 7:
METHODOLOGY:
2.2 Traffic Light LEDs
Each road is equipped with a set of LEDs:
Red LED → Stop 
Yellow LED → Transition 
Green LED → Go 
Total:
Road A → 3 LEDs 
Road B → 3 LEDs


Slide 8:
METHODOLOGY:
2.3 7-Segment Display
Displays the countdown timer for the active green signal. 
Helps simulate a real-world traffic light timer. 

2.4 LCD (16x2, I2C)
Displays system status such as: 
“Road A: GO” 
“Road B: GO” 
Remaining time in seconds


Slide 9:
METHODOLOGY:
3. Software Design and Code Logic:
The system is implemented in embedded C using Arduino IDE, structured into modular functions:

3.1 Distance Measurement
Function: long readDistance(int trigPin, int echoPin) 
Operation: Sends a 10µs pulse, measures echo return time, calculates distance as Distance = Time × 0.034 / 2 
Purpose: Determines vehicle proximity on each road.


Slide 10:
METHODOLOGY:
3.2 Traffic Comparison Logic
Compares distances from Road A and B with ±5 cm tolerance: 
Equal Traffic: Both roads get 10s green each 
Road A Priority: Road A gets 10s green, Road B 5s 
Road B Priority: Road B gets 10s green, Road A 5s 

3.3 Traffic Light Control
Road A Control: roadA_Green(int time) → Green_A ON, Red_B ON, countdown, Yellow_A for 2s 
Road B Control: roadB_Green(int time) → Green_B ON, Red_A ON, countdown, Yellow_B for 2s


Slide 11:
METHODOLOGY:
3.4 Countdown Timer
Function: countdown(int t) 
Updates 7-segment display (last digit) and LCD (full seconds) every second using delay(1000). 

3.5 7-Segment Display Logic
Function: displayDigit(int num) 
Uses a byte digits[10][7] array to control segments and display digits 0–9.


Slide 12:
METHODOLOGY:
4. System Operation Flow
System initializes all pins and display modules. 
Ultrasonic sensors continuously measure vehicle distance. 
Microcontroller compares traffic density on both roads. 
Decision is made based on predefined conditions. 
Corresponding road is given green light priority. 
Countdown timer is displayed. 
Yellow light transition occurs before switching roads. 
Process repeats continuously in a loop.


Slide 13:
Methodology:
5. Circuit Schematic Overview
5.1 Sensor Connections
TRIG pins → Output pins of microcontroller 
ECHO pins → Input pins 
5.2 LED Connections
Each LED connected to GPIO pins through resistors 
Separate pins for Red, Yellow, Green for each road 
5.3 7-Segment Display
7 GPIO pins connected to segments (a–g) 
Controlled using digital HIGH/LOW signals 

Slide 14:
METHODOLOGY:
5.4 LCD (I2C)
Connected via: 
SDA → Data line 
SCL → Clock line 
Uses I2C protocol for efficient communication

6. System Characteristics
Adaptive: Adjusts signal timing based on real-time traffic 
Efficient: Reduces waiting time and congestion 
Scalable: Can be extended to more roads or sensors 
Low-cost: Uses simple sensors and LEDs



Slide 15:
SIMULATION:

Slide 16:
SIMULATION:


Slide 17:
SIMULATION:


Slide 18:
CONCLUSION:
Conclusion
This project successfully designed and implemented a Smart Traffic Light System capable of dynamically adjusting signal timings based on real-time traffic conditions at a two-way intersection. By integrating ultrasonic sensors, a microcontroller, and visual display units, the system was able to monitor vehicle proximity and prioritize roads with higher traffic density.
Summary of Findings
The results obtained from both design and simulation demonstrate that:
The system effectively detects traffic density using ultrasonic sensors. 
Adaptive timing allows roads with higher vehicle concentration to receive longer green light durations, improving traffic flow. 
The use of a 7-segment display and LCD enhances system transparency by providing real-time countdown and status information. 
Compared to conventional fixed-time systems, the proposed system reduces unnecessary waiting time and improves overall efficiency at intersections. 


Slide 19:
CONCLUSION:
Challenges Encountered
During the development and simulation of the system, several challenges were identified:
 
Limited Traffic Representation: The system estimates traffic using distance rather than actual vehicle count, which may not fully reflect real-world conditions. 
Timing Constraints: The use of delay-based timing (delay() function) reduces system responsiveness and;\ prevents simultaneous task execution. 
Simulation Limitations: The simulation environment does not perfectly replicate real-world traffic behavior, such as continuous vehicle movement or unpredictable conditions.


Slide 20:
CONCLUSION:
7. Limitations of the Approach
Only considers distance, not exact vehicle count 
Suitable for low to medium traffic intersections 
Limited to two-road intersection in current design 
Delay-based timing (delay()) may reduce responsiveness
8. Possible Improvements
Replace ultrasonic sensors with camera-based detection 
Add multiple sensors per lane for better accuracy 
Integrate with IoT/cloud systems for smart city applications


Slide 21:
CONCLUSION:
Final Remark:
Overall, the Smart Traffic Light System demonstrates a practical and cost-effective solution for improving traffic management in low to medium traffic intersections. With further enhancements, it has the potential to be deployed in real-world smart transportation systems, contributing to reduced congestion, improved travel time, and better urban mobility.

