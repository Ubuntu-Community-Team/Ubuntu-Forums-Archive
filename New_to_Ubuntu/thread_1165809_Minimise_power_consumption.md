---
title: "Minimise power consumption"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by GXice on 2009-05-21
I've got a very bare-bones desktop system running on relatively powerful hardware (AMD Athlon 5000 X2). Installed is some RAM, two hard drives and a DVD-ROM.

The purpose that I'm using Ubuntu for now, I don't need all this power. Other than underclocking via BIOS, is it possible to somehow turn on "battery-saver" mode for a desktop so that it reduces power consumption?

---

### Post by nhasian on 2009-05-21
does your CPU support frequency scaling?  if so, right click on your taskbar and select Add to Panel.  Choose CPU Frequency Scaling Monitor.  You need to do this for each core.  now if you click on it on the taskbar you can lower the frequency of your cpu which uses less energy and runs cooler

---

### Post by GXice on 2009-05-21
> **nhasian said:**
> does your CPU support frequency scaling?  

I'm not sure, how can I check?

---

### Post by mcduck on 2009-05-21
> **nhasian said:**
> does your CPU support frequency scaling?  if so, right click on your taskbar and select Add to Panel.  Choose CPU Frequency Scaling Monitor.  You need to do this for each core.  now if you click on it on the taskbar you can lower the frequency of your cpu which uses less energy and runs cooler
There should be no need for this. If the CPU supports frequency scaling, it's used automatically. And the default mpode is "Ondemand" which drops to minimum speed when possible, and jumps directly to full speed when more CPU power is needed. This is the mode that saves most power in normal use.

GXice: just add the applet to your panel, and you should easily see if yur CPU changes it's speed automatically or not. Or run "cat /proc/cpuinfo", or just tell as what CPU you have and we'll tell you if it supports powersaving or not.

Pretty much every fairly new AMD & Intel CPU supports frequency scaling.

---

