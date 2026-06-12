---
title: "Ubuntu 9,04 very slow lately on my PC - why?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-08-09
Hey,

when I first installed Ubuntu 8.10 64-bits on my PC in March, it ran fast as hell. Now I have 9.04, and it started out pretty fast, but lately, this PC has been slow, mostly regarding the graphics.

I have desktop effects (compiz) enabled, and I'm using the 185.18.14 NVidia drivers which I installed as described in Kosimo's thread ("nVidia latest Drivers - How to install - (180.xx - 185.xx - 190.xx)"). Minimizing/maximizing windows is jerky, rebuilding them on screen takes its time, so does e.g. opening new tabs in Nautilus or Firefox. Also, streaming videos has become a slideshow.

I wonder why that is? One thing is that my \ partition, which has 4 GB, is almost full. There are a bit more than 100 MB left (when I first installed, I read that 4 GB is more than plenty for the system parition, I now realize that it is waaay too little if you want to keep installing updates). Could that be the reason?

Another thing is that whenever a new Linux kernel is released, I have to re-install the graphics drivers. Do you guys have the same issue, and could there be a connection between that and the slow graphical performance?

Thanks!

---

### Post by The Bright Side on 2009-08-09
In fact, I just installed the new Nvidia driver (.31), which partly fixed this (I had overlooked its release, just found out about it). The performance is better now, but still not what I had when I started out. Did my system just get cluttered and hence sluggish over time? I thought this only happened in Windows?

---

### Post by halitech on 2009-08-09
if the / partition is down to 100meg free that could be causing some slow down. I usually give about 10gig to /

how much ram and what is the speed of your cpu?

---

### Post by The Bright Side on 2009-08-09
It's an Athlon 64 X2 5200+ (DualCore) with 4 GB of RAM.

---

### Post by Crunchy the Headcrab on 2009-08-09
> **The Bright Side said:**
> 
Another thing is that whenever a new Linux kernel is released, I have to re-install the graphics drivers. Do you guys have the same issue, and could there be a connection between that and the slow graphical performance?

This is normal and shouldn't cause any slowdown.  You compile your driver for a specific kernel.  When you have a new kernel installed you thus need to reinstall your driver.  BTW, if you download the driver from Ubuntu's repository by using the built in Hardware Driver installer you won't have to reinstall the driver, as the driver will automatically be updated when the kernel is updated.  However, you are not going to get the latest driver this way.

---

