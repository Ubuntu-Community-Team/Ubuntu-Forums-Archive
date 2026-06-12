---
title: "Noob question - can I compile wl module from jaunty for Lucid ??"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by wozzy123 on 2010-05-07
Hi There,
 
I have tried installing the new Lucid release - everytihng seems ok except wifi.
 
 
I have a dell mini 1510 wireless n pci-e card- (broadcom bcm4322 I think). In lucid + network manger - connecting using wpa2/aes is hit and miss. (wireless n only / 40 mhz channel )
 
normally, it requires removal of the sta module (rmmod wl -> followed by modprobe wl). After serveral retries, it connects, however speeds are too slow -> around 20 mbps or less (show in my router, network manager shows only 2 mbps)
 
In jaunty, this card works out the box (from fresh kernel install from live cd -> plus any subsquent kernel images for jaunty). It uses the same wl module. I can see connection speeds of 230 - 270 mbps from the same router and 34 -54 mbps in network manager.
 
 
SO is this possible, using the same module from jaunty and compile it for lucid instead ??
 
 
Or is this not possible due to underlying changes to how the kernel works and interactions with network manager ??
 
 
Or is this something network manager related causing problems? 
 
 
I have tried b43 module using fw cutter but does not work at all on Lucid. WICD gave me much less performance on jaunty. -
 
So i have everything running v.well on jaunty. Is there anyway to replicate this on Lucid. 
 
 
Thanks in advance,
 
 
Ezyn.

---

### Post by blazemore on 2010-05-13
If you know the name of the module, you can try to load it with the command:
```
sudo modprobe **modulename**
```

---

