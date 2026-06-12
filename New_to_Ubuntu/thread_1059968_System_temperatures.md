---
title: "System temperatures"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Andy06 on 2009-02-04
What's the best way to read temperatures of CPU, RAM, HDD, GPU etc

Screenlets only give me ACPI and GPU. X sensors doesn't work. I think im missing some backend package that these use to read the temperatures off. I've installed lm sensors, but not sure what front end do I use to read the temperatures.

Thanks

---

### Post by LowSky on 2009-02-04
Do you really need to monitor all those temperatures? Is your computer a nuclear reactor? Seriously, are you doing intensive CAD or some kind of Folding project or does your computer need a air conditioner to run porperly?

but this post should help I guess

> **NoReflex said:**
> I use Ubuntu Hardy so gnome is my window manager - for hardware monitoring I use Hardware Sensors Monitor (it displays CPU temp (on both cores and individually), GPU temp and hddtemp (had to install nvidia-settings and hddtemp for the last two)). If I remember right you must install lmsensors.
I also added to my panel the System Monitor applet which gives informations on the system load.
If you use KDE you should go with superkaramba (it has a lot of themes and looks good).
Hope this gives you a starting point.

Best wishes,
NoReflex

---

### Post by Malta paul on 2009-02-04
Hi, I use temp sensors as I've over clocked my system and keep an eye on things.
May be this will help:
1) sudo apt-get install subversion
2) sudo sensors-detect   [for LM-sensors]
3) using Synaptic package Mgr.
    a) sensor - applet
    b) LM-sensors
    c) right click 'add to panel

Have fun ;)

---

### Post by Andy06 on 2009-02-04
LOL, no I'm just a numbers whore and like to keep an eye on everything I possibly can. Im also a sucker for eye candy and have conky set up along with various screenlets and ringmeters to let me know my bandwidth, total upload/download, RAM usage, Swap, CPU1, CPU2, disks, IP addresses, SSID, exncryption, main processes blah blah blah:D

---

### Post by Kellemora on 2009-02-04
Hi Andy

You sound about as bad with computers as I was with cars back in the 60's n 70's......  I had thermal sensors on everything, even including the differential and axle hubs.
I would nearly have a heart attack every time one of them was out of range of normal, even though no reason was ever found for it.
Probably a faulty sensor reading is all!

Down at the graphics studio, they actually have a Chiller (package AC unit fed to the CPU's) to keep their processors cool.  In their case, it's not overkill though, hi hi...........

TTUL
Gary

---

### Post by Andy06 on 2009-02-05
I can still only get CPU, GPU and ACPI temperatures. I really want the HDD or RAM temps as well.

How do I read info off the hddtemp thing I installed on synaptic.

Also how to install Hardware Sensors Monitor? Did not find it either in synaptic or add/remove.

Thanks a lot

---

### Post by Malta paul on 2009-02-05
You might like to check out:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

;)

---

