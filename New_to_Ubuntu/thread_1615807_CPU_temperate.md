---
title: "CPU temperate?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by interceptorV8 on 2010-11-07
as a birthday present to myself as well as a little "goal" to work toward during the mandatory overtime we had to put in at work, i decided to build my first computer.  ultimately i went with:

motherboard: ASRock 880gxh
cpu: AMD x6 1055t
corsair h50
4gb ddr3 ram

when installing the H50, some of the pre-applied thermal paste easily rubbed off from my several attempts at mounting it over the cpu. i applied a dab of the thermal compound i bought from best buy.  i read that too little and too much is bad so i'd like to know ASAP if i need to take apart this machine and reapply the paste.

i am currently running ubuntu 10.10 and i'd like to know the most accurate cpu temperature.

i have 'xsensors 0.70' installed and i get readings from the various voltages, fans, temp1, temp2, and temp3, though i am not sure which temp is referring directly to the cpu.  at the moment - temp1: 37C, temp2: 32C, temp3: 103.5C.  which is which?

i also have k10temp installed and i am not sure how accurate it is since all of these temps are different. ktemp at idle reads anywhere from 16C-20C

the temp in the bios averages at 40C

---

### Post by bioterror on 2010-11-07
I get:

> $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +20.0°C  (crit = +127.0°C)                  
temp2:       +45.0°C  (crit = +127.0°C)

So this makes sense that your temp1 & temp2 are CPU's and temp3 is your hard drive, or something else.

I've got laptop with Intel U2500 dual core and the both cores are around 40-50C

---

### Post by pme 72 on 2010-11-08
You could also try lm-sensors. I did not save the post I used for installation instructions but did save part of the text:

"I dont have an intel system to test with at the moment, but in so far there is a thermal sensor in the gpu, I suspect you can read it with lm-sensors. Install lm-sensors and sensors-applet. Then in a terminal run

sudo sensors-detect

Follow the instructions, and select Y on every question. When its done, reboot and add sensor-applet to your panel and configure it, or check in the terminal with "sensors"."

Those instructions allowed me to have the cpu temps displayed on the upper panel of my AMD based desktop. Both lm-sensors and sensors-applet were available from the Software Center in Lucid, 10.04. For more information do an Internet search for lm-sensors and you will find many posts.

---

### Post by Megaptera on 2010-11-08
Is this guide any help?

[http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/](http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/)

---

### Post by pkjm17 on 2010-11-13
I too don't know which temperture temp1, temp2, and temp3 represents. This is my sensors output. 

pat@pat-desktop:~$ sensors
it8720-isa-0228
Adapter: ISA adapter
in0:         +0.99 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.94 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.34 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.93 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +1.89 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.30 V
fan1:       1394 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +28.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +41.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.250 V

---

