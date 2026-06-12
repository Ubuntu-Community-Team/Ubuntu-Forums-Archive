---
title: "upgraded to 7.10 and now wireless card doesnt work"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by marq on 2007-10-07
i made the move to the new beta version of ubuntu, just because i couldent wait and wanted to have the new gnome, anyways now my wireless card wont work, and im running live cd so i guess any info i tell u wont help other then it's a D-link WDA-1320 (which is a pci card and works out of the box in 7.04)

i dont know if this has already been solved and an update will fix it if i can get a wired connection

i dont know if this has been solved in another post, but if anyone knows id be happy to be redirected 

please any bit of information helps, thanks in advance

---

### Post by marq on 2007-10-07
bump

anything helps ppl

---

### Post by kevdog on 2007-10-07
Can you post the following:

lspci -nn
lshw -C network

My guess is that the drivers are no-longer built-in, or you need to install the restricted-drivers package for your kernel.

---

### Post by marq on 2007-10-07
marq@marq-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV6 [Vanta/Vanta LT] [10de:002c] (rev 15)
02:04.0 Ethernet controller [0200]: Atheros Communications, Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
02:09.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 08)
02:09.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 08)

marq@marq-desktop:~$ sudo lshw -C network
[sudo] password for marq:
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:08:02:5a:4c:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.0.104 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

hope that helps

---

### Post by marq on 2007-10-07
note: im not running live cd anymore, i moved the computer downstairs for a wired connection temporarily, so i could get updates on the current system

---

### Post by kevdog on 2007-10-07
Ok, your card is supported by the madwifi drivers which you must have installed when you installed Feisty.  What you want to do is first determine your kernel version. At command line:

uname -r

That will give the kernel version.

Then go into Synaptic and do a search for linux-restricted.   Match the linux-restricted-modules to the version of your kernel.  Install the package and then reboot.  You should be good to go.

---

### Post by marq on 2007-10-07
hey that did the trick 1000 thanks

---

