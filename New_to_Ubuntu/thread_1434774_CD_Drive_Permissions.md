---
title: "CD Drive Permissions"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by MDFa on 2010-03-20
Hey Im new to Ubuntu, or linux for that matter. Its working wonderfully except for my CD drive is detected but will not open CD's or DVD's. Im guessing that since it is in my Computer file browser it is already mounted. I was wondering if anyone had experienced this or knew how to fix this problem..

A few more details..

running Ubuntu 10.04
drive is recorded as CD/DVD drive, under properties and permissions it says "the permissions of CD/DVD Drive could not be determined".
8X DVD-Super Multi double-layer drive

---

### Post by FreezWay on 2010-03-20
what does lspci give you

---

### Post by MDFa on 2010-03-21
I am really now at this, what is ISPCI?

---

### Post by rokumanxes on 2010-03-21
LSCPI

Applications > Terminal >
then type lscpi and press enter, and give the results.
Hope that helps.

---

### Post by MDFa on 2010-03-21
It says command not found?

---

### Post by 3rdalbum on 2010-03-21
Are you talking about audio CD and video DVDs, or data discs?

The command asked for is, in lowercase, LSPCI. That's a lowercase L, a lowercase S, a lowercase P etc. But I don't see how it will help.

---

### Post by MDFa on 2010-03-21
Im talking about both, The CD will be recognized if it is in the machine during start up, and i can see the file.. but if i change the cd or remove the cd after i have logged into ubuntu I can no longer access the drive or see the files/watch the movie etc.

---

### Post by MDFa on 2010-03-21
the lspci gave me this..

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

