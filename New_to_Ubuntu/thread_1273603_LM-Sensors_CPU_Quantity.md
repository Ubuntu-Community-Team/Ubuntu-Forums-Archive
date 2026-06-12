---
title: "LM-Sensors CPU Quantity"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by gallam on 2009-09-23
I installed LM-Sensors and am using a widget layer to monitor processor load. I have a Quad Core processor. While it sees all of the cores, and each is reporting a different and varying load depending upon the task, there is a fifth processor that shows up. Thus, the CPUs are labeled 0, 1, 2, 3 and 4. What is the 4th processor? Could it be the graphics card CPU that the sensors are seeing? This isn't a big deal... Just curious.

---

### Post by swoody on 2009-09-25
I believe one of those (possible CPU0) is your overall CPU usage. So four of the CPU monitors are for each core individually, and one for your overall usage. Take a closer look at them all, and see if the numbers work out, and you can figure out which is which. If not, I'll have to look into this a bit deeper to find out what it is :)

---

### Post by XCan on 2009-09-26
Perhaps the unknown one, be it 0 or 5, is the sensor on your mobo or heatsink? Intel specify their maximum operating temperature measured on the geometrical center of the heatspreader, and not the individual die temperatures. So it would make sense that one of your sensors would reflect that in some way.

Just to add, on my Q9450, I don't have such a sensor, I'm on an Asus P5QL PRO.

---

