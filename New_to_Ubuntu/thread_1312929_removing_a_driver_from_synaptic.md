---
title: "removing a driver from synaptic"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-03
Hi, 
I've freshly installed 9.10 and Hardware Drivers has found 2 NVIDIA graphics card drivers; recommending I install "173". However, i have experience of installing this driver, then, the tolerable default scrn res of 800x600, dropping to 600x4800 and opens a NVIDIA Display settings gui which it seems is to big to manipulate om my crt monitor. 

600x480 res soon becomes a strain on my eyes, so i want to be able to remove 173 if i can't solve the prob in one session. Will 173 show up as one pkg i can remove in synaptic?

Thanks

---

### Post by Phil D. on 2009-11-03
Have a look in System-Administration-Hardware Drivers, there you can remove/install drivers

---

### Post by liquidbee on 2009-11-03
```
 
dpkg -l | grep nvidia

```
 
All of them can be removed in the same way as you installed them.

---

