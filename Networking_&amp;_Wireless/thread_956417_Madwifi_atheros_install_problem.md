---
title: "Madwifi atheros install problem"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by Karilex on 2008-10-23
Hello I have a compaq c700 with an atheros wireless I've recently installed ubuntu and noticed that the wireless wasn't working so I looked around and found this: [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)
I followed the instructions and everything works fine until i type make into the terminal and i get this(yes i am a newb):
~/madwifi-ng-r2756+ar5007$ make 
make: *** No targets specified and no makefile found.  Stop.

So if anyone could help me with that i would be very grateful

---

### Post by Karilex on 2008-10-24
bump

---

### Post by melojo on 2008-10-24
I downloaded the tar file and the only thing it contains is a read me file and this is what it says

> You most likely downloaded this tarball since you are looking for a version
of MadWifi which supports the AR5007 chipset family, which is for example
used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

If you have any questions about it, please contact our regular support
channels:
[http://madwifi.org/wiki/Support](http://madwifi.org/wiki/Support)

Thanks.

---

### Post by melojo on 2008-10-24
open a terminal and post the output of

sudo lshw -C network

---

### Post by Karilex on 2008-10-24
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:a3:2b:7c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by orre64 on 2008-10-24
I have the same card and I cant get it to work either. I'll be checking in on this thread for a solution.

---

### Post by melojo on 2008-10-24
Have a look here, read through the posts.

[http://ubuntuforums.org/showthread.php?t=766169&page=2](http://ubuntuforums.org/showthread.php?t=766169&page=2)

---

### Post by Karilex on 2008-10-25
thanks a lot=D>=D>=D>=D>

---

### Post by orre64 on 2008-10-25
You got it working..??

---

