---
title: "System Monitoring"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Khrimzunn on 2009-07-06
Is there a program that lets me see all temperatures and fan speeds on my machine? I've been using speedfan for windows, but since I switched over I'm not sure if there is anything like it. 
The program I am thinking of would have the ability to show the fan speeds, and temperatures of critical system components equipped with a temperature sensor. Also it would be helpful if I can use it to manually set fan speeds without having to go trough bios every hour or so.

Screenshot of speedfan and the unbelievable temperature readings in the attachment. 
Yeah I know, I know, it's insanely hot. That's why I want to see if it's speedfan, or my system is a fire waiting to happen. I have a hunch that it's wrong, since there is no way my system temperature is close to the boiling point of water.

So any help or hints?

---

### Post by iver2435 on 2009-07-06
I seem to recall a command called "acpidump" or something like that that allows you to look at fan speed and temperature information.

You can search for commands related to acpi by running:
```
apropos acpi
```
at the command prompt.

There is also the /proc/acpi folder that I believe contains information about what you're looking for.

---

### Post by ainsworth_t on 2009-07-06
I've never used it, but check out the lm-sensors package, should do what you're looking for.

---

### Post by Yvan300 on 2009-07-06
I would recommend hard info, it's in the repositories. It is very similar to everest and will tell you all that you need to know and more, including benchmarking.

---

### Post by Khrimzunn on 2009-07-06
I can't find hard info or everest in the packages, I installed lm-sensor, but I'm still looking to figure out where it is and how to use it. Thanks for the info.

---

### Post by jimsheep on 2009-07-06
i'm using lmsensors, and it's great.  search Google using:
```
lmsensors ubuntu
```
to get instructions for installation and sensor detection.  very nice interface, too.

---

### Post by Yvan300 on 2009-07-06
1.Make sure that you have universe, and multiverse packages enabled in synaptics,
2. When searching for hard info, it is spelt 'hardinfo' not 'hard info'. Oh and you might not see it in Add/Remove.
3. Everest is a windows only program that i was just using as a comparison.

---

### Post by Khrimzunn on 2009-07-06
Thanks, well I am going to try that too, so far I'm running lm-sensors. and, this is not making sense...
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)                  

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.13 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +6.28 V  (min =  +1.90 V, max =  +2.32 V)   ALARM
AVCC:        +3.33 V  (min =  +0.45 V, max =  +0.21 V)   ALARM
3VCC:        +3.33 V  (min =  +1.97 V, max =  +0.29 V)   ALARM
in4:         +1.09 V  (min =  +0.26 V, max =  +1.86 V)   
in5:         +1.55 V  (min =  +1.86 V, max =  +1.02 V)   ALARM
in6:         +5.86 V  (min =  +4.66 V, max =  +4.63 V)   ALARM
VSB:         +3.33 V  (min =  +1.47 V, max =  +3.22 V)   ALARM
VBAT:        +3.14 V  (min =  +3.66 V, max =  +3.68 V)   ALARM
Case Fan:      0 RPM  (min = 84375 RPM, div = 16)  ALARM
CPU Fan:    2518 RPM  (min = 14062 RPM, div = 8)  ALARM
Aux Fan:       0 RPM  (min = 84375 RPM, div = 16)  ALARM
fan4:          0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan5:          0 RPM  (min = 168750 RPM, div = 8)  ALARM
Sys Temp:    [COLOR=Red]**+88.0°C**[/COLOR]  (high =  +0.0°C, hyst = +127.0°C)  sensor = thermistor
CPU Temp:    +39.5°C  (high = +127.0°C, hyst =  +0.0°C)  sensor = transistor
AUX Temp:    +42.5°C  (high = +127.0°C, hyst =  +0.0°C)  sensor = thermistor
cpu0_vid:   +1.450 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +57.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +54.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +52.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +56.0°C  (high = +80.0°C, crit = +100.0°C) 
```How the hell do I get those temperatures when I'm not running anything very demanding?
EDIT: Also, I have two fans that are not connected to the designated fan connections on the board, they are connected to the PSU. Not sure if that helps.

---

### Post by CLomax on 2009-07-06
88c? That looks quite inaccurate to me, especially since the other temps are much lower. Could be a faulty temp sensor.

Were those readings taken at idle? If they were you may have bad airflow in your case.

You mentioned that some fans aren't in their designated slots, why is that?

---

### Post by Khrimzunn on 2009-07-06
> **CLomax said:**
> 88c? That looks quite inaccurate to me, especially since the other temps are much lower. Could be a faulty temp sensor.

Were those readings taken at idle? If they were you may have bad airflow in your case.

You mentioned that some fans aren't in their designated slots, why is that?
Yeah I know something is not right, after leaving it off for a few hours I for the same readings almost, except the 88 turned into 90. It makes no sense. 
The fans, they came with the connections to the power supply since they are case fans, my computer is custom built. It can't be bad air flow because I have cleaned it already and it was bought early this year. 
I don't think you'll need any specs but just ask if you want to know.

---

