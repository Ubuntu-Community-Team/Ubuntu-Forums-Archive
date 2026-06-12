---
title: "xsensors problem"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Achilles124 on 2011-04-24
I have a question about xsensors. For temperatures I get three outcomes:
35 degrees
43 degrees
127 degrees (!)

That is way too much. That is why the last figure is in the red. Questions: 
- Of what devices are these temperatures taken? 
- And in particular, of what device is the third temperature taken?

Thank you beforehand.

---

### Post by khelben1979 on 2011-04-24
Can you confirm the readings of the temperatures from within your [BIOS]("http://en.wikipedia.org/wiki/BIOS")? If not, I would definitely guess that 127 degrees (if accurate) that it comes from your graphic card, those have a tendency to get hot.

Graphic cards can go way beyond 127 degrees, but it can damage it if it's not constructed to manage the heat. I think it's way too hot as well, does not look good.

---

### Post by Achilles124 on 2011-04-26
These are the reading I get from the BIOS:
> CPU temperature: 45 degrees Celcius
System temperature: 44 degrees
CPU fan speed: 3105 RPM
sys fan 1 speed: 0 rpm
sys fan 2 speed: 0 rpm
CPU Vcore: 1360 V
3.3V:  3280 V
5V: 5003 V
12 V: 11.968V
5V SB: 5.045V

Other information:
> CPU voltage: 1.3250V
Memory voltage: 1.90
NB voltage: 1250
VTT FSB  voltage: 1200
SB i/0 power: 1.5
SB core power: 1.05

I am no expert so I don't know what it all means. The CPU voltage seems odd to me.

---

### Post by Achilles124 on 2011-04-26
Here is a screenshot of the preferences of the gnome-sensors-applet. It is temp 3 that is so high and on the face of it, it is not the graphical card that is causing the trouble. Not the graphical card, not the core. So, what else?

---

### Post by Achilles124 on 2011-04-26
I forgot to add the screenshot. Here it is:

---

### Post by khelben1979 on 2011-04-28
I think that as long as your computer is working OK you shouldn't be too worried about some software which spits out some numbers. Do you got any hardware problems over there? And if not, then you got no problems.

I think if the BIOS reports numbers which isn't so good, then you got bigger problems, but I couldn't see any problems from what you listed in this thread.

---

### Post by Achilles124 on 2011-04-28
Yes, I do have problems, khelben1979. I use Puppy Linux now because my computer sometimes doesn't boot the way it should.

[http://ubuntuforums.org/showthread.php?t=1707998]("http://ubuntuforums.org/showthread.php?t=1707998")

That is why I checked the temperature within my computer.

---

### Post by khelben1979 on 2011-04-29
I quickly read through that thread and I'm wondering if you have looked inside for dust to see if it needs some cleaning? Having it clean in there reduces the temperature and keeps it cooler.

---

### Post by Achilles124 on 2011-05-01
Okay, ty for your answers, khelben1979. I will give it a shot.

---

### Post by Achilles124 on 2011-05-01
Cleaned my computer thoroughly. No result: temperature is still 127 degrees.

---

### Post by Achilles124 on 2011-05-08
I read a little more about sensors and this is what I get from the terminal after typing "sensors":

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +86.0°C, crit = +100.0°C)  

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:       +3.28 V
in1:         +1.23 V  (max =  +2.04 V)   
in2:         +1.64 V
in3:         +0.96 V
in4:         +0.95 V
in5:         +1.10 V
in6:         +1.51 V
3VSB:        +3.28 V
Vbat:        +3.22 V
fan1:       2097 RPM
fan2:          0 RPM  ALARM
fan3:          0 RPM  ALARM
fan4:          0 RPM  ALARM
temp1:       +27.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +50.0°C, hyst = +46.0°C)  sensor = transistor
temp2:       +30.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp3:      +124.0°C  (high = +70.0°C, hyst = +68.0°C)  ALARM  
                      (crit = +85.0°C, hyst = +83.0°C)  ALARM  sensor = thermistor


```

So, what is the thermistor. It is the motherboard, isn't it?

---

### Post by jave on 2011-05-17
> **Achilles124 said:**
> So, what is the thermistor. It is the motherboard, isn't it?

Hi,

Could well be. What motherboard model is it?  Could you possibly beg/borrow/steal a similar model from someone else to try out with your CPU/RAM for a test to see if the white lines appear?

I know you've memtested the RAM, but can you borrow any other RAM to try out and test?

Jave.

---

### Post by gordintoronto on 2011-05-17
> **Achilles124 said:**
> I have a question about xsensors. For temperatures I get three outcomes:
35 degrees
43 degrees
127 degrees (!)

That is way too much. That is why the last figure is in the red. Questions: 
- Of what devices are these temperatures taken? 
- And in particular, of what device is the third temperature taken?

Thank you beforehand.

Have you installed hddtemp? 35 looks like a hard drive. 127 looks like a memory location which is not a sensor at all. Does your video card (which one?) support temperature reporting? Have you ever used lm-sensors, and its sensors-detect?

---

### Post by pablolie on 2011-05-17
have you carefully touched different locations on your build to see which part gets that hot? can you provide mobo model and graphics card (if included)?

---

### Post by Achilles124 on 2011-05-19
I will take a look.

---

