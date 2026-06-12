---
title: "can't get wireless internet connection to work"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by fixmetwo on 2010-10-02
I'm new to linux

HP laptop w/AMD 64 cpu
installed ubuntu lucid (dual boot win XP)
bcm4311 wlan (works on XP)
2Wire wireless modem

I have spent days reading and trying things.
I installed ndiswrapper pkg with bcm.inf and .sys files
that went ok driver installed but it will not connect(wireless disconnected)
what am I missing?

I haven't had this much fun sense win 3.1 hardware install.

I'm stumped- don't know where to go from here.

---

### Post by Hippytaff on 2010-10-02
guess you've read this :-) [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by fixmetwo on 2010-10-02
yes but i'll go through it again

---

### Post by lifelike27 on 2010-10-02
I had the same problem when I initially installed Ubuntu 10.04 on my laptop. 

You have to connect your laptop to a wired network first and let it download the Broadcom drivers for your wireless card. It'll probably also download the video card drivers as well. These are proprietary drivers which aren't open to the Ubuntu community  (because the manufactures are twits?) so they aren't pre-installed.

---

