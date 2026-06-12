---
title: "[SOLVED] Fileshare(Xubuntu and Windows)"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by tbrminsanity on 2006-11-15
I have a Compaq Armada 1750 running Xubuntu that I want to network with my desktop (running Win2K).  I'm having trouble getting it to work, neither computer will see each other.  They are connected through a cross over cable.  Samba is loaded on Xubuntu.  What else do I need to do?

The main goal of this is to quickly class notes between the two computers (instead of using a USB flash drive like I have been so far).

---

### Post by dbbolton on 2006-11-15
go to your shared folder on the xubuntu box

right click > share folder > general windows share settings

then select "this computer is a wins server".


on your windows computer-

control panel > network connections > right click your lan connection> properties

then select "internet protocol (tcp/ip)" and click Properties > Advanced > WINS

add your IP in the top box, and at the bottom, select "enable netbios over tcp/ip"

reboot.

---

### Post by tbrminsanity on 2006-11-16
Thanks.  Worked like a charm

---

