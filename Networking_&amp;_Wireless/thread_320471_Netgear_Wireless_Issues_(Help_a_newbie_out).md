---
title: "Netgear Wireless Issues (Help a newbie out)"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Darkbladedancer on 2006-12-17
I'm having a problem with my Netgear wireless card. I have a Netgear WG511U PCMCIA card for my laptop. 

Anyway, here's the problem.

I've installed the drivers and 'sudo ndiswrapper -l' reads both the drivers and the hardware present. In the ubuntu help file for installing these though, it says I have to run the following lines in the terminal

sudo depmod -a
sudo modprobe ndiswrapper

'sudo depmod -a' works fine as far as I know, the terminal doesn't return anything.

'sudo modprobe ndiswrapper' returns the following, which is my problem.

'FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17.10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid arguement.

Help me out, what should I do?

---

### Post by compwiz18 on 2006-12-17
Try running: **sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.8**

---

