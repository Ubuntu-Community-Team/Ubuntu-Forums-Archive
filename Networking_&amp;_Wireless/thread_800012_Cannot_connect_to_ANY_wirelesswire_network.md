---
title: "Cannot connect to ANY wireless/wire network"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by XedGeneral on 2008-05-19
I have Ubuntu 8.04...

Running on a IBM ThinkPad T60
-Intel Core 2 Duo 1.86GHz
-ATI Radeon Mobility X1300
-1GB 667MHz RAM
-Intel Wireless Pro 3945ABG 


Wireless: I can detect a lot of networks, both encyrpted and un-encyrpted. But I can't connect to ANY wireless network!

Wired: When I plug-in a network cable, my computer doesn't respond at all, and there was no internet at all!


I am a noob, just started using Ubuntu. Can anyone help me? :KS

---

### Post by Iowan on 2008-05-19
Dunno if it's chanbed in Hardy, but earlier versions of N-M would not activate more than one interface.  you can see if eth? (wired) is active - or verify the existance of an "auto eth0" line in **/etc/network/interfaces** file.

---

