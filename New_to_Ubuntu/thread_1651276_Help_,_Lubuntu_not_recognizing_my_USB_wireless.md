---
title: "Help , Lubuntu not recognizing my USB wireless"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Mikaelo1 on 2010-12-22
I have a Belkin USB wireless adapter I don't know how to make it work with lubuntu please help.  Is not showing nm-applet
** (nm-applet:1756): WARNING **: <WARN> constructor(): Couldn't initialize the D-Bus manager.

---

### Post by Mikaelo1 on 2010-12-22
A user of this forum trying to help another suggested this to be written in a terminal so it would be easier to help him. 
Code:
lspci -nnlsusblshw -C Networkuname -asudo iwlist scandmesg | grep -e b43 -e iwl -e rtl -e wlan
In tried it  and this is what came up
 
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] [1002:5157]
02:0c.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
&#12288;
&#12288;
&#12288;
--------------------------------
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:615a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
----------------------------------
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: 82540EM Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: c
bus info: pci@0000:02:0c.0
logical name: eth0
version: 02
serial: 00:0b:db:3e:12:09
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 mingnt=255 multicast=yes
resources: irq:18 memory:ff6e0000-ff6fffff ioport:dcc0(size=64)
----------------------------------
Linux miguel-OptiPlex-GX260 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
&#12288;
----------------------------------
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
----------------------------------
&#12288;
&#12288;
&#12288;
&#12288;I separated each code with --------------- this line

---

### Post by Mikaelo1 on 2010-12-23
I forgot the last one:
 
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
Bus: primary=00, secondary=02, subordinate=02, sec-latency=32

---

### Post by davidmohammed on 2010-12-23
this guy says that he resolved this by doing the stuff described in post #5 of this [thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1546667").

---

### Post by pytheas22 on 2010-12-23
> A user of this forum trying to help another suggested this to be written in a terminal so it would be easier to help him.
Code:
lspci -nnlsusblshw -C Networkuname -asudo iwlist scandmesg | grep -e b43 -e iwl -e rtl -e wlan

I was probably that user, I think...I remember typing those commands recently :)

In any case, from the output you posted, it looks like Ubuntu does not currently have any driver available to drive your wireless card.  The instructions in post #5 of the thread that davidmohammed links to above should get it working, however, using the ndiswrapper driver.  Please give those a try and let us know if it solves the problem.  If it still doesn't, please post back with the output of these commands:
```

ndiswrapper -l
dmesg | grep -e ndis -e wlan
lshw -C Network
sudo iwlist scan
```

(For what it's worth, I don't think that step #1 of the instructions listed in that other thread should be necessary at all, but it also shouldn't hurt anything in your case, so you can try it if you want.  The other three steps are definitely necessary.)

---

