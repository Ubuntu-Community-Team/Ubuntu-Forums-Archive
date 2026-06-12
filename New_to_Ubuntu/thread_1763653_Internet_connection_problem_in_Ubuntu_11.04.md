---
title: "Internet connection problem in Ubuntu 11.04"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by solongsoho on 2011-05-20
I have Ubuntu 11.04 and i have a little issue concerning my internet connection. I have DSL connection with Ethernet cable. I usually take my laptop with me when I go out and when I return home I have to reset the operating system once.
To make my internet connection I wrote ```
sudo pppoeconf
``` in terminal so I can't connect normally by clicking a "Connect" button as for the Wireless internet. If I reset it once the internet connection works, until, of course, I pull the cable out, having to reset it once.
My guess is that when i first open the laptop it doesn't recognize the NIC.
I would like to know if I can do something to overwhelm this and to not being obliged to reset the laptop every time I come home.
Thank you

---

### Post by josephmills on 2011-05-20
could you please post ```
lspci -nn
``` thanks

---

### Post by grahammechanical on 2011-05-20
It seems to me that you are issuing a command to start the connection and then not switching the connection off before you unplug the cable. Is this so? Is this why you need to reset the computer when all you should need to do is plug the cable back in and type sudo pppoeconf in a terminal to connect again.

I used to use a dial up modem and I started the connection with sudo pon and ended the connection with sudo poff.

What is the command for disconnecting pppoe?

Regards.

---

### Post by solongsoho on 2011-05-21
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

---

### Post by solongsoho on 2011-05-21
I didn't thought it this way. I will try to see what happens.

Later edit:
It works now with ```
sudo pon dsl-provider
``` after i turn on my pc. I really didn't knew I had to kill my connection every time I want to pull the cable out.
Thank you for the hint.

---

