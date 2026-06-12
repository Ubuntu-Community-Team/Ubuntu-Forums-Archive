---
title: "lm-sensors help"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by pkjm17 on 2010-11-12
Hi,

Can someone explain which temperature Temp1, Temp2, Temp3 represents? Like, which one is my CPU and MB temperature? Here is my out from running sensors. Also, does anyone know the scrip to use for displaying the CPU and MB temps in Conky?

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
fan1:       1236 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +26.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +39.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.250 V

---

### Post by nishant.singh28 on 2010-11-12
> **pkjm17 said:**
> Hi,

Can someone explain which temperature Temp1, Temp2, Temp3 represents? Like, which one is my CPU and MB temperature? Here is my out from running sensors. Also, does anyone know the scrip to use for displaying the CPU and MB temps in Conky?

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
fan1:       1236 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +26.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +39.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.250 V

AMD CPU so I'm not very sure you'll get the CPU sensors to work...but see if you can. As of now, they are not being read.
As for temp1, 2 and 3, you can load different parts of the hardware like using glxgears to heat up the GPU, transferring file to HDD to heat up Southbridge and doing some thing that takes up both CPU and memory to heat up the Northbridge(Intel guy here so translate terms accordingly ;))
As for conky, you can use hwmon to get the the data. Google around that a bit.

---

### Post by snuffy47 on 2011-01-05
Bump

I have just installed ImSensors and have a Temp 1, 2, 3 and would like to know what they are also.

My Temp 3 seems high at boot up and it would be nice to know what it is.

I also have an AMD CPU

---

### Post by cchhrriiss121212 on 2011-01-05
Lm-sensors can show anything from cpu, mobo, gpu or anything else. Try using inxi -F it is much easier to read. Get the package from here:
[http://code.google.com/p/inxi/](http://code.google.com/p/inxi/)

---

### Post by Frogs Hair on 2011-01-05
You can display temps on the gnome panel with description by installing the hardware sensors monitor and activating it from the add to panel menu. It has options to display as text , icons , or graph.
 
```
sudo apt-get install sensors-applet
```

---

### Post by snuffy47 on 2011-01-05
I have the temps displayed in the panel but the descriptions are only Temp 1,2,3
I also have Fan speeds visible

It has raised some concerns for me as Temp 3 is high but I have no idea what it is

Thinking it might be the southbridge chip

---

### Post by sandyd on 2011-01-05
The CPU temps should look like (I have a dual core non-mobile Core2Duo in a laptop with cpufreqd, so it looks cooler than a laptop should)
```

coretemp-isa-0000
Adapter: ISA adapter
**Core 0:**      +65.0 C  (high = +90.0 C, crit = +90.0 C)  

coretemp-isa-0001
Adapter: ISA adapter
**Core 1:**      +62.0 C  (high = +90.0 C, crit = +90.0 C)  

```

Apparently, lm-sensors can only get cpu temperature from coretemp, which is only for intel processors.

---

### Post by sandyd on 2011-01-05
> **snuffy47 said:**
> I have the temps displayed in the panel but the descriptions are only Temp 1,2,3
I also have Fan speeds visible

It has raised some concerns for me as Temp 3 is high but I have no idea what it is

Thinking it might be the southbridge chip
knowing what is is won't make any difference unless your planning on placing dry ice on that very spot, or installing a fan at that spot.

---

### Post by Mark Phelps on 2011-01-06
> **sandyd said:**
> Apparently, lm-sensors can only get cpu temperature from coretemp, which is only for intel processors.
It may not work for SOME non-Intel processors, but until a couple of days ago, I was running it on an AMD 939 processor -- and it worked fine.

---

### Post by snuffy47 on 2011-01-06
@ sandyd
This system is in a DIY DVD case for a HTPC so I want to make sure that it isnt poor air flow.

There may be a requirement to add a fan but I need to know what it is.

I am not an expert Ubuntu user, but have installed it on 2 of my windows machines and enjoy it.  It is just alittle frustrating not know how to do things :(

---

### Post by mcduck on 2011-01-06
lm-sensors really is just a simple tool that reads raw data from whatever sensors it can find on your motherboard, it doesn't know what those sensors are or how the information should be interpreted to provide meaningful readings. Telling it what each value is,  how they should be calculated from the raw data, and what min/max limits there should be is something you need to do yourself.

So, your best option is to compare the readings from lm-sensors to those you see in your BIOS or any tool provided by your motherboard's manufacturer, and then adjust /etc/sensors.conf to get matching readings from lm-sensors.

Without any data to compare the readings from lm-sensors to, anybody trying to tell you what those values are would just have to make a guess (and assume none of the values needs to be divided by two to get the true value, or something like that). :D

It's like this because there really is no standard how the sensors on motherboards are implemented. Of course you could try to search with google if anybody has already made a sensors.conf file for your motherboard...

---

