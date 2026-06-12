---
title: "Network Card"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Timoteo32 on 2010-01-10
Anyone know why all my wireless networks would disappear all of the sudden? I can't connect to anything, even if I type the name of the network in.  I'm running Ubuntu 9.04 on a laptop.  Any ideas on how to fix it?  Please help :(

---

### Post by phidia on 2010-01-10
You might want to see if a friend's laptop will find your network but if you're sure the network is functioning then use the guide [here]("http://ubuntuforums.org/showthread.php?p=6183681") to try and determine what's up.

---

### Post by Timoteo32 on 2010-01-10
A) My roommate's laptop works fine
b) all the neighbor's networks disappeared from the list too :(

---

### Post by Timoteo32 on 2010-01-18
Really??  No one knows how to fix this or what it might be??

Does anyone know a better place to go to find the answer?

---

### Post by ubudog on 2010-01-18
> **Timoteo32 said:**
> Really??  No one knows how to fix this or what it might be??

Does anyone know a better place to go to find the answer?

Are you sure your wireless is enabled?  Post the output of lspci.

---

### Post by Timoteo32 on 2010-01-18
Is that like ipconfig for windows?

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

It's pry something easy but I don't know how I did it or how to fix it :(

---

### Post by ubudog on 2010-01-19
It looks like you have a broadcom card.  If you are on 9.04 or 9.10, go to System>Administration>Hardware Drivers and see if there is a driver in there.

---

