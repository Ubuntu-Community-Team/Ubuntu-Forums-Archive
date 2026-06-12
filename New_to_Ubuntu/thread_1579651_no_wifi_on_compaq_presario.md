---
title: "no wifi on compaq presario"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by zabergan on 2010-09-22
I'm trying to put ubuntu 10.04 on a friend's computer (Compaq Presario V5000) because windows xp stopped working. I wiped out xp and tried to install ubuntu. I had some problems at first but after 4 or 5 goes I managed to get it up and running but I can't get wifi to work.

---

### Post by nothingspecial on 2010-09-22
You need to post your wireless card
```

sudo lshw -C network
```

Post the output here

---

### Post by zabergan on 2010-09-22
*-network:0             
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:06:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 
       resources: irq:21 memory:c0200000-c0201fff 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:06:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:d4:02:1e:a8 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s 
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:14:a5:a4:00:da 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by nothingspecial on 2010-09-22
First get a wired connection and have a look in System > Administration > Hardware Drivers

There should be something in there

If not, try

```
sudo apt-get install b43-fwcutter
```

Then restart

---

### Post by lkraemer on 2010-09-22
Try this HOWTO:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=V5201us](http://ubuntuforums.org/showthread.php?t=1470146&highlight=V5201us)

lk

---

### Post by zabergan on 2010-09-22
Thanx a lot for your help!

Followed this link and now wifi is working perfectly

[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

---

