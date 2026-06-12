---
title: "Setting up Wireless Internet"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by forcemultiplier on 2008-09-04
Hi! I'm new to Ubuntu and I would really appreciate it if someone could help me with setting up my wireless internet on my laptop.

I have configured my laptop to dual boot with Windows Vista Premium as my other OS.

I did play around with Network Settings and all but couldn't really do anything useful..

I'm like stuck.. I read through the topics provided in the Help Menu.. but I can't find Hardware Settings to find the drivers.. stuff like that.. I'm groping around in the dark..

I'd appreciate it if someone could come up with some advice to help me out of this predicament.

Thanks

FM

---

### Post by Kevbert on 2008-09-04
Welcome to Ubuntu.
Regarding wireless, we need to find out what chipset your wireless adapter is using.  Please go to Applications-Acessories-Terminal and enter the following commands:
```
lspci
iwconfig
```
Then using the mouse highlight the outputs for each command and select Ctrl-Shift-C to copy the output and Ctrl-V to paste the output here.  The problem is that you may need to install some firmware drivers for your wireless.

---

