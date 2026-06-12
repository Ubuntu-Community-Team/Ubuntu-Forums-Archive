---
title: "help finding correct wireless driver patch for injecting with aircrack?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by jarongg on 2009-03-06
i would like to know what driver patch i need (from this list, i think: [http://patches.aircrack-ng.org/](http://patches.aircrack-ng.org/)) for my msi wind u100, for use with aircrack ng. thanks .

---

### Post by jarongg on 2009-03-07
bump.

---

### Post by jarongg on 2009-03-08
tops.

---

### Post by plucky on 2009-03-09
You have given no information for us to help you,that is probably why you have had no replies.

Open a terminal and post output of ```
lshw -C network
``` which will display your network card and driver.

---

### Post by WaNaBePi on 2011-08-15
same question...sorry its an old thread...
```
default@default-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1b:b1:4f:a5:38
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.114 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fc600000-fc603fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:d1:72:ab
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:34 memory:fc700000-fc703fff ioport:4000(size=256) memory:fc200000-fc21ffff(prefetchable)
default@default-laptop:~$ 

```
Thank you!

---

### Post by kieths on 2011-10-11
First...I'm no expert, but I google a lot...


Based on your current wireless card's driver and version, it looks like your WiFi card is a BCM4312 Broadcom card, or similar.  If that is correct, you would be looking for the bcm 43xx driver patches.

Hope that helps in some minor way.

---

