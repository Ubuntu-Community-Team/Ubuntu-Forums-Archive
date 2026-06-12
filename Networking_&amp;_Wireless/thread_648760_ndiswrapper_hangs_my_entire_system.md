---
title: "ndiswrapper hangs my entire system"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by Melcar on 2007-12-24
I'm having a weird issue with ndiswrapper.  The problems started after I changed my motherboard from a nforce4 based board to a X580 board.  Before I was able to use ndiswrapper very easily, either from the repos or by compiling the latest version; it always worked.  Now, I can still install it successfully, but every time I try to load it (either by rmmod of by restarting) it hangs my whole system.  If I have the module load at start-up, the kernel will hang when it tries to load it.  The only way I can then manage to log back in is to remove my wireless adapter (or remove ndiswrapper from the modules list).  The device I'm using is an Airlink101 AWLL3055 (usb adapter), but as I said, it has always worked before.

---

### Post by kevdog on 2007-12-24
Can you post

ndiswrapper -l

---

### Post by Melcar on 2007-12-24
Doing that either hangs my system (most of the time) or just shows the driver that's installed (doesn't show the device, despite it being plugged in).

---

### Post by kevdog on 2007-12-24
lshw -C network

---

### Post by Melcar on 2007-12-24
Right now I'm just using the kernel module:
> 
 *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:a3:03:ff:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.110 multicast=yes wireless=IEEE 802.11b/g


It doesn't specify (weird) but the module is zd1211rw.  ZD1211BU.INF is the Windows file I have always used (it's the only one anyway).

---

