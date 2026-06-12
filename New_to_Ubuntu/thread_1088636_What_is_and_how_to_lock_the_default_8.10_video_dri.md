---
title: "What is and how to lock the default 8.10 video driver?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by bettyhills on 2009-03-06
The Nvidia driver for my system (see specs below) permits only 800x600 max resolution so I prefer the 8.10 default video driver.  

I would like to LOCK the default in place to prevent update manager from overriding the default with the latest Nvidia driver.

Can anyone tell me:
1.  The default video driver **filename** in 8.10?
2.  How to lock it so that it never changes?

TIA

---

### Post by Paqman on 2009-03-06
> **bettyhills said:**
> 
Can anyone tell me:
1.  The default video driver **filename** in 8.10?


The default open source driver is called nv. The proprietary ones you get through Hardware Drivers are called nvidia-glx-1XX.

> 
2.  How to lock it so that it never changes?

You can lock any package through Synaptic. Pull up the package in Synaptic and click Package > Lock version.

---

### Post by bettyhills on 2009-03-06
I apologize. I did not ask my question clearly.

xserver-xorg-video-nv is the default Nvidia driver that I do NOT want.  Its max resolution is 800x600.  I am trying to prevent Update Manager from continually installing newer versions of Nvidia drivers.  I do not want them.

When I delete the Nvidia driver, Ubuntu 8.10 reverts to the generic default driver that allows me to select higher screen resolutions.  

I need the **filename** of the **generic** default Ubuntu 8.10 video driver so that I will know which one to lock.  

Synaptic lists thirty-seven installed video drivers including:
xserver-xorg-video-intel 922KB 2:2.4.1 1ubuntu10.3 intel i8xx,i9xx display driver. This has the ubuntu logo by it.
xserver-xorg-video-i810 250KB 2:2.4.1 1ubuntu10.3 intel i8xx,i9xx display driver.  This does not have the ubuntu logo.

Thanks in advance for any advice on how to proceed.

---

### Post by Paqman on 2009-03-07
The very, very generic driver is vesa, but i'd be surprised if that gave you any decent screen resolutions either.

---

