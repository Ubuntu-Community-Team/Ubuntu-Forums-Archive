---
title: "Trying to get new nvidia drivers to work"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by alienexplorers on 2009-03-27
I am trying to either load the 173.14.18 or the 96.43.11 driver and all I keep getting is low graphics mode.  I have made sure I have the nvidia driver option listed in the xorg.conf file.  If someone has gotten these drivers to work I would really like to know how to do it.  Thanks in advance.
Donald

---

### Post by blazemore on 2009-03-27
How are you installing the drivers? Are you using the Nvidia .run file, or the included utility?

---

### Post by alienexplorers on 2009-03-27
I am using the nvidia run files off the nvidia web site.

---

### Post by Paqman on 2009-03-27
It's a lot easier to just go to System > Admin > Hardware Drivers and use that.

---

### Post by alienexplorers on 2009-03-27
On my system that still shows the old drivers.

---

### Post by Paqman on 2009-03-27
> **alienexplorers said:**
> On my system that still shows the old drivers.

What versions? You might also want to try using [Envy](apt:envyng-gtk), it's the easiest way to get more up-to-date drivers than you get from Hardware Drivers.

---

### Post by alienexplorers on 2009-03-27
Envy still has the old versions of these drivers.  I guess I will have to wait for ENVY to be updated.

---

### Post by Paqman on 2009-03-27
What version are you after?

---

### Post by alienexplorers on 2009-03-27
173.14.18 or the 96.43.11 driver

---

### Post by Paqman on 2009-03-27
That's odd, the Intrepid repo shows that it has 71, 96, 173 and 177 in it. Have you definitely got the Restricted repo enabled?

---

### Post by 3rdalbum on 2009-03-27
Intrepid Backports has a 180.xx driver - just do a search in Synaptic Package Manager for "180" and it will pop up. If it doesn't pop up, then you need to enable the Backports repository in System > Administration > Software Sources.

---

### Post by Paqman on 2009-03-27
> **3rdalbum said:**
> Intrepid Backports has a 180.xx driver

+1. The 180 series drivers are a huge improvement over the 170s.

---

### Post by blazemore on 2009-03-27
If you really want the most recent version, get 180.
The latest stable version is in the Restricted Drivers manager.

---

### Post by R33D3M33R on 2009-03-27
The 180.x driver is not available for Geforce FX 5200 (source: nvidia download site)

---

### Post by blazemore on 2009-03-27
Okay Download it to your home directory.

Write this down:

Switch to another TTY with CTRL + ALT + 1
Log in with your credentials
Type sudo su to become root
type```
/etc/init.d/gdm stop
``` to kill the X session.
browse to your home folder with ```
cd /home/username/
```
type ```
chmod +x *.run
```
type ```
./*.run
```

---

### Post by Britmonkey on 2009-03-27
I've got the same problem as original poster.
I've followed Blazemores instructions above but get the following:

> NO Precompiled kernal interface was found.
do you want to download a kernal from nvidia?

[yes]

no matching precompiled kernal interface was found on Nvidias ftp site.  
this means installer will need to compile a kernal interface for your kernal.

[ok]

ERROR you do not appear to have libc header files installed.
please install your dist libc development package.

ERROR: Inst has failed please see file /var/log/nvidia-installer.log. 

Can anyone suggest the name of the package I need to install?

Thanks for reading.

---

### Post by Britmonkey on 2009-03-28
Ok I figured out how to install the libc header files.

> apt-get install build-essential 

run in su terminal got me the required files.

The nvidia installation then seemed to run through ok.

However when restarting i get a message saying you are running in "low graphics screen" you need to configure your screen.
I try this with all obvious combinations of open source and generic drivers which look applicable to a FX5200, but i cant get anything higher than 800x600 resolution on a 21" screen.

Any other thoughts out there,  anyone actually got the FX5200 to work with ubuntu?

---

### Post by Britmonkey on 2009-03-28
FX5200
Think I found the resolution in another thread.  

[http://ubuntuforums.org/showthread.php?t=1106912&highlight=fx5200](http://ubuntuforums.org/showthread.php?t=1106912&highlight=fx5200)
post #6 by upchuky.

Thanks to all those who took the time to read.

---

