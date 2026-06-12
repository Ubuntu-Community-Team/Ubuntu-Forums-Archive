---
title: "&quot;Detect Display&quot; fails"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by DrSkylaser on 2010-04-25
Hey guys, I'm trying to get Karmic to work with a dual monitor setup, but the display-detect fails utterly (both with my original monitor and the secondary monitor).  I've found a couple of threads about how to set up VNC monitors, but as a total n00b I'm not sure how much of that applies.  I've tried to figure out what driver it's using by System --> Administration --> Hardware Drivers, but it just says " no proprietary drivers are in use on this machine".  (My primary monitor is a Gateway FHX2300.)

---

### Post by quadproc on 2010-04-25
> **DrSkylaser said:**
> ...  I've tried to figure out what driver it's using by System --> Administration --> Hardware Drivers, but it just says " no proprietary drivers are in use on this machine".  (My primary monitor is a Gateway FHX2300.)
The Hardware Drivers utility does not necessarily correctly report the status of the system.  I quit using it when I learned this.

I would suggest that you look in the /etc/X11/xorg.conf file to see which driver is listed in there.  Something like```
 grep "river" < /etc/X11/xorg.conf
``` should show one and only one Driver line which is not commented out.  If that line indicates vesa then you have a very simple and basic driver, if it indicates ati then you have an open source ATI driver, if it indicates fglrx then you have ATI's proprietary driver.  Sorry, I don't know what the nvidia driver names are.

quadproc

---

### Post by DrSkylaser on 2010-04-25
I read somewhere that Karmic got rid of xorg.conf--no?  In any case, my machine doesn't seem to have one.

---

### Post by quadproc on 2010-04-25
> **DrSkylaser said:**
> I read somewhere that Karmic got rid of xorg.conf--no?  In any case, my machine doesn't seem to have one.
The xorg.conf file is now optional.  If X windows doesn't find one then it looks at the hardware and makes its best guess for running things.

If you do install an xorg.conf file then the X server will use it.  That would allow you to specify as much deatil as you want for your system.

quadproc

---

