---
title: "network settings in virual box"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by go_beep_yourself on 2007-10-21
How can I configure this? I want to use it instead of NAT.

---

### Post by Hero of Time on 2007-10-21
So, you want to bridge your eth0 to your virtual machine, correct? Then you need to look at something different. You need to create a new interface, set that in VirtualBox and use a bridge package to bridge it to eth0. I've seen a topic around here that explains how to run Windows seamless using RDP which required a bridged connection. Just follow the bridge part and you should be running in no time.

---

### Post by go_beep_yourself on 2007-10-21
What topic? Where is it? Yes, I am trying to bridge.

---

### Post by Hero of Time on 2007-10-21
How about using the search option for once in a while? They you would have seen this: [http://ubuntuforums.org/showthread.php?t=433359&highlight=seamless+xp+virtual+box](http://ubuntuforums.org/showthread.php?t=433359&highlight=seamless+xp+virtual+box)
Although it's written voor Edgy, it will still work the same way.

---

