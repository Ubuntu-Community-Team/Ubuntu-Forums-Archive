---
title: "Screen 1280x1024 loses top panel on Dell E4300"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-11-03
I had 1280 x 1024 running on my 19' Dell monitor attached to my Dell laptop under Jaunty and Intrepid. Under Karmic, when I set this resolution on my monitor, the top and bottom panels are lost!!

What am I doing wrong?

---

### Post by techningeer on 2010-07-17
I have a similar problem, but this is on Ubuntu 10.04 LTS. I recently  upgraded manually from 7.10 to 10.04 on this computer. Most of the  settings imported just fine. However, there is a problem with the screen  being slightly cut off on all sides except the top. Because I have had a  similar problem with this computer and monitor, I did what I did  before: "System>Preferences>Monitors" (in 7.10, it would have been  "System>Preferences>Screen Resolution"). I am using a Dell Vostro  200 PC with a Dell 19" E207WFP monitor.

After having read several different threads on similar subjects, I found  one that tells me how to detect my graphics card, which is having  problems also. (View [http://ubuntuforums.org/showthread.php?t=1339113&highlight=dell+19%26quot;+monitor+driver]("http://ubuntuforums.org/showthread.php?t=1339113&highlight=dell+19%26quot;+monitor+driver")  post no. 2). Following the instructions on detecting the graphics card,  this is what I get:

> *-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:fdf00000-fdf7ffff ioport:ff00(size=8  memory:d0000000-dfffffff(prefetchable) memory:fdc00000-fdcfffff
Also, I can't use the "Extra" visual effects I should be able to .

It does have the correct resolution for the monitor , but detects it as a Dell  20" monitor.

Here are  the Dell Specs:

Highest/Optimal preset resolution        1680 x 1050 at 60 Hz 

Any help is greatly appreciated(If you need more info, just let me know!)!

---

### Post by techningeer on 2010-07-17
Also, when switching user or sitting for a long time, it turns black and freezes sometimes.

---

### Post by jtarin on 2010-07-17
[Xrandr]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") could be your solution....in most cases it is.We have no actual xorg.conf file in todays Ubuntu, so this shows how.

---

### Post by techningeer on 2010-07-21
jtarin, I appreciate your reply. However, I don't quite understand what "xrandr" does and why. Is it something like SaX on SuSE and RedHat, or is it like the "xfree86config" command? I am used to administering systems that use the XFree86/X11/XWindows system, literally configuring from scrathc in the config file. Is x.org similar?

Any help is appreciated!

-techningeer

---

### Post by jtarin on 2010-07-21
> **techningeer said:**
> jtarin, I appreciate your reply. However, I don't quite understand what "xrandr" does and why. Is it something like SaX on SuSE and RedHat, or is it like the "xfree86config" command? I am used to administering systems that use the XFree86/X11/XWindows system, literally configuring from scrathc in the config file. Is x.org similar?

Any help is appreciated!

-techningeerI hear ya! Same here. I've been running Slackware since version-6 and have always made my xorg corrections the old-fashioned way....editing. 
**From the link I gave you:**> X RandR is used to configure which display ports are enabled (e.g. LCD, VGA and DVI), and to configure display modes and properties such as orientation, reflection and DPI.

This is the simplest and most powerful way to get multi-monitor systems working using recent versions of Linux such as Ubuntu 7.10 and Fedora 8 with graphics chipsets such as the Intel 945GM/GMS and ATI Radeon found in Thinkpads.

xrandr is the command line interface to the RandR X extension. As usual with X, good documentation is hard to find; first try the following commands: 
All I can do is point you to a possible solution as I have the Intel 945GM/GMS chip for video and have experienced no problems running Ubuntu or Kbuntu. Issue the command ```
lspci 
```to see what chipset your using and thenthe command ```
lsmod
```to see ifthe correct module is loaded for that chipset. It shoud be i915. There is no xorg.conf file generated in these newer distros....but my understanding from various searches is that it is possible to generate one and use it, if you so desire.

---

### Post by techningeer on 2010-08-27
jtarin, I fixed the problem with the screen being cut off by adjusting the monitor's settings. Some other problems still remain. I am going to take a copy of SuSE linux 6.2 and "renovate" it.
Thanks again for your advice!

---

