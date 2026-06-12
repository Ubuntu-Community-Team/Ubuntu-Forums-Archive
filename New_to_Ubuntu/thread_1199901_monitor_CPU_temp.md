---
title: "monitor CPU temp"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by insanity99 on 2009-06-29
i recently OC's my CPU and need to keep an eye on my temp, how do i do this using ubuntu?

---

### Post by philcamlin on 2009-06-29
[http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)

this is a good thing to use :) :popcorn::popcorn:

---

### Post by insanity99 on 2009-06-29
i fail'd already, when i copy the command into the terminal i get this:
neil@ubuntu:~$ apt-get install lm-sensors
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
neil@ubuntu:~$ 

why is this?

---

### Post by philcamlin on 2009-06-29
you have to put sudo in front of that to run it as root :)

sudo apt-get install lm-sensors :)

:popcorn:

---

### Post by blur xc on 2009-06-29
If you are into the geeky side of seeing what you computer is doing, search the fourm for "conky".  I've got mine set up to display cpu temps of both cores, video card temp, hdd temp, cpu loading, mem usage, etc...etc...
 
It's kind of fun to setup- infinitely customizable.
 
BM

---

### Post by insanity99 on 2009-06-29
now i get this: neil@ubuntu:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lm-sensors is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lm-sensors has no installation candidate

---

### Post by philcamlin on 2009-06-29
sudo apt-get install sensors-applet :popcorn:

---

### Post by insanity99 on 2009-06-29
sorry to be a pain but this time it's
neil@ubuntu:~$ sudo apt-get install sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sensors-applet

---

### Post by philcamlin on 2009-06-29
umm 

go into synaptic

click all available applications

and sype in sensors and click X sensors :)

---

### Post by insanity99 on 2009-06-29
thanks i have the software but it's just a blank window

---

### Post by Arup on 2009-06-29
Go to [www.medibuntu.org](www.medibuntu.org) and check how to enable repos. Then do a sudo apt-get install lm-sensors hddtemp after install a terminal will pop up for hddtemp, say yes to all options, then do a sudo sensors-detect and say yes to all options and then enter twice. I use gkrellm as front end to monitor temps and volts as well as other options, you can do a sudo apt-get install gkrellm 

Reboot and fire up gkrellm from system tools and you will find all the sensors listed, in case you have nvidia or ati card with their drivers loaded, you will see the GPU temp as well.

---

