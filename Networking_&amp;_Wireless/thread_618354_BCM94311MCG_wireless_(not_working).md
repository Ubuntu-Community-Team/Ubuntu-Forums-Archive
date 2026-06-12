---
title: "BCM94311MCG wireless (not working)"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by phouse on 2007-11-20
Hello.  I recently installed Ubuntu on my Dell Latitude D830 and I am unable to get my wireless working.  I've followed a few threads but there's some differences on my laptop from what's described in those threads and I'm uncertain what to do next.  My laptop has a BCM94311MCG wireless adaptor and my lshw -C network has the following description for my wireless card:

```
*-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:60:47:d8:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

lspci gives a more succinct but affirmative output as well to the type of wireless card I have.  If I do ifconfig eth1 up, I get:  ```
SIOCSIFFLAGS: No such file or directory
```

My guess would be that the wrong drivers are installed but I'm not really sure as to what I am looking at.  I am uncertain as to what to do next and any help would be greatly appreciated.

---

### Post by phouse on 2007-11-20
Well, I don't know why I didn't get a response other than it looks like laptops and wireless are still far and away very raw with Linux, even with a polished distro like Ubuntu.  Thanks anyhow I suppose.  I was hoping to spend less than an hour or two trying to fix any sort of problems post-install.  I've met that limit.

---

### Post by NosLycn on 2008-07-09
Hi. It's not that wlan is far away.  It's that broadcom is far away and Dell is farther away for using an unsupported chipset in their products while trying to pass themselves off as "Linux-friendly".

I'm working on the same problem with an Inspiron 1521 right now.  It's my mother's computer.  I got her to switch to Linux.  She loves it.  She hates Windows.  But, because she can't be near an ethernet hook-up, she is going to switch to Windows again.

But, I must stress that I have no such problems with my Intel 3945 A/B/G wireless and people with Atheros chipsets have far fewer problems.  It's Broadcom and Dell.

---

