---
title: "I must be getting stupider (wireless problem)"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2009-12-27
About a week ago, I installed wubi 9.10 in my aspire 5000. When the wireless refused to work, I started this thread:

[http://ubuntuforums.org/showthread.php?t=1358180](http://ubuntuforums.org/showthread.php?t=1358180)

asking for advise, and then, thanks to those who replied to it, I got my wireless working in no time at all.

Now, I decided to get rid of windows, so, after reinstalling ubuntu, I tried to get my wireless to work again, and for the life of me I CAN'T DO IT!!!:-x

Just as before, I ran the sudo lshw -C network routine, and this is what I got:

 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:ee:00:ad
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.102 latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:28000000-2801ffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2000000-e2001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:4b:a4:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

I tried downloading ndiswrapper from the software center, and it tells me it's "not available in the current data", tried with the synaptic package manager and it can't find it, and finally downloaded it from the web and it won't install!

And, to make things worse, I can't find a bcm4318 driver to save my life.

Please, if anybody can help me before I go completely crazy I'd greatly appreciate it.

Thanks in advance.:)

---

### Post by spiderbatdad on 2009-12-27
the link supplied in the above post is broken. You'll need a temporary wired connection to install the driver.

---

### Post by Inodoro Pereyra on 2009-12-27
Just fixed the link. Sorry...

I do have a wired connection. But I can't find a single driver that'd work. I must have downloaded 1/2 dozen of them already...:(

---

### Post by 3rdalbum on 2009-12-27
You need to reload the package list. On your wired connection, go into Synaptic and hit the Reload button.

After completing this, close Synaptic and open Hardware Drivers. Check to see if there's a driver offered there. If not, then you should be able to find Ndiswrapper in Software Centre or Synaptic and you can follow the procedure you did before.

---

### Post by Inodoro Pereyra on 2009-12-27
WOOOOOWEEEEEEE!!!

THANK YOU 3rdALBUM! 
It's working perfectly now.

Phheewwww...!
Thank you.!

---

### Post by 3rdalbum on 2009-12-27
> **Inodoro Pereyra said:**
> WOOOOOWEEEEEEE!!!

THANK YOU 3rdALBUM! 
It's working perfectly now.

Phheewwww...!
Thank you.!

You're welcome.

---

