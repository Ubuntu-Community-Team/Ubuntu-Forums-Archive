---
title: "bcm43xx dropping connection/timing out"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by cubfan400 on 2007-08-29
I have the broadcom bcm4311 chipset and used the bcmfwcutter tool to get the card semi-working.  it is recognized, and i can configure it, but it connects to the network, lets me browse the web for maybe a minute and a half then the connection to the web vanishes.  network manager still shows that i'm connected to the network however.  i have found that i can buy myself another minute and a half by doing modprobe -r bcm43xx then modprobe bcm43xx, but that is such a pain.  is there any way to make it work properly???

---

### Post by bmartin on 2007-08-30
Use ndiswrapper. [Here's a thread]("http://ubuntuforums.org/showthread.php?t=405990") with a graphical installer. Or you can do it manually; I recommend using [this thread]("http://ubuntuforums.org/showthread.php?t=297092") if you want to do it step-by-step.

The firmware isn't 100% at this point. I had the same problem as you using a BCM4318 chipset. I've never had my connection drop since switching to ndiswrapper, and my signal strength and speed are great.

---

