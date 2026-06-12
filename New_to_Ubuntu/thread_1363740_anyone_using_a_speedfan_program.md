---
title: "anyone using a speedfan program?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by chemgrl08 on 2009-12-24
Greetings. I am a new user; just switched to  ubuntu for my main computer AND for my netbook (and let me just say I am very pleased!) My computer has a problem with overheating. and I was aware of it prior to using ubunutu. I do plan to fix it when I get the time (yes yes I know fry my hard drive blah blah) but I am looking for a program in the meantime that will monitor my CPU temperature and fan speed. When I had windows XP, I was using speedfan, but it appears that it does not support linux. I have also searched in the software center but I seem unable to find exactly what I'm looking for. Just want a simple program, nothing fancy. Any recommendations?
Thanks, and my apologies if this is in the incorrect f1orum. Inform me of where it should be and I will repost it as appropriate Thanks!

---

### Post by Sef on 2009-12-24
Moved to ABT.

---

### Post by bruno9779 on 2009-12-24
install sensor-applet

```
sudo apt-get install sensor-applet
```

then right click on the upper bar and choose Add.

then search for "temp" and add the only entry. That should take cae of the CPU monitoring. Dunno about fan control though

---

### Post by bruno9779 on 2009-12-24
You could read this [http://linux.die.net/man/8/fancontrol](http://linux.die.net/man/8/fancontrol)

It is maybe a little too advanced, and the author discourages its casual use.

---

### Post by cartisdm on 2009-12-24
I have noticed that Linux distros don't handle my fan very efficiently and my laptop will run very hot.  Windows 7 is actually worse so I was forced to install a 3rd party control that runs in the background and keeps it at a cool 30 degrees celsius.  I haven't found anything in Ubuntu that will work quite as well though

---

### Post by bruno9779 on 2009-12-25
maybe this helps [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by chemgrl08 on 2009-12-27
I tried the first thing you recommended but I got the message "couldn't find package sensor-applet"
instead I tried to add it from the software center, and I found x sensors program which, according to the description should work. However, when I open the program it just shows a blank window- I don't know how to add temperature feature. I tried right-clicking on the window and on the bar on top, but it didn't give me the option "add."
 I really just want to monitor the temp; I'm not really concerned about fan speed.

---

### Post by SecretCode on 2009-12-27
It's 'sensor_s_-applet' I think.

After installing it I also installed lm-sensors and ran 
```
sudo sensors-detect
service lm-sensors start
sensors -s
```

Then added the "Hardware Sensors Monitor" applet to my gnome panel.

---

### Post by mhousel on 2009-12-28
> **bruno9779 said:**
> install sensor-applet

```
sudo apt-get install sensor-applet
```

then right click on the upper bar and choose Add.

then search for "temp" and add the only entry. That should take cae of the CPU monitoring. Dunno about fan control though


#sudo apt-get install sensor-applet
Reading package lists...Done
Building dependency tree...
Reading state information...Done
E: Couldn't find package sensor-applet
#

Now what?

---

### Post by doas777 on 2009-12-28
> **mhousel said:**
> #sudo apt-get install sensor-applet
Reading package lists...Done
Building dependency tree...
Reading state information...Done
E: Couldn't find package sensor-applet
#

Now what?

correct the spelling as shown above.
sensor[SIZE=4]**s**[/SIZE]-applet

---

### Post by mhousel on 2009-12-28
> **doas777 said:**
> correct the spelling as shown above.
sensor[SIZE=4]**s**[/SIZE]-applet


That's what I get for copying text from a quote box! :(

Thank you!


Oops got too excited too quick!


root@mhousel-laptop:/var/run# apt-get install sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sensors-applet is already the newest version.
The following packages were automatically installed and are no longer required:
  librrd4 xautomation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mhousel-laptop:/var/run#  sensors-applet
sensors-applet: command not found

It somehow thinks it's already there, yet it's not really there?

---

### Post by doas777 on 2009-12-28
sensors applet is a gnome-panel applet, so to show it, right click on a blank peice of panel, and select Add to Panel. then scroll down to Hardware Sensors Monitor (or somesuch), and it will appear. then rclick->Properties to configure which sensors to show.

---

### Post by mhousel on 2009-12-28
> **doas777 said:**
> sensors applet is a gnome-panel applet, so to show it, right click on a blank peice of panel, and select Add to Panel. then scroll down to Hardware Sensors Monitor (or somesuch), and it will appear. then rclick->Properties to configure which sensors to show.

Thanks, so that works and shows the same data the the kSensors panel shows.  
So I think that lm-sensors is working OK, but my system seems to have very few sensors?

But nothing allows me to **speed up my fans** above the minimum until just before the system clicks off with an over temperature.

The limits here seem to be unchangeable by any means I can find or example shown anywhere.

My sensors output looks *nothing* like anything posted anywhere?

root@mhousel-laptop:~# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +55.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by doas777 on 2009-12-28
> **mhousel said:**
> Thanks, so that works and shows the same data the the kSensors panel shows.  
So I think that lm-sensors is working OK, but my system seems to have very few sensors?

But nothing allows me to **speed up my fans** above the minimum until just before the system clicks off with an over temperature.

The limits here seem to be unchangeable by any means I can find or example shown anywhere.

My sensors output looks *nothing* like anything posted anywhere?

root@mhousel-laptop:~# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +55.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (high = +100.0°C, crit = +100.0°C)

yeah, I've always been disappointed at the sensors exposed to linux. even speedfan is iffy on less common hardware. my last 3 HP business machines at work, won't even show the core temps in speedfan with vista/win7.

---

