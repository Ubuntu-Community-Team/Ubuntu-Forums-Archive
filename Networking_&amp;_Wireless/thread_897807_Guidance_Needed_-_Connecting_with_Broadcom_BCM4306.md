---
title: "Guidance Needed - Connecting with Broadcom BCM4306 (ver 03)"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by Theberge43 on 2008-08-22
Hi, 

I have in the past tried to install Ubuntu on my desktop at home and I always end up changing my mind because of the freaking wireless connection.

So, I have a fresh install of Ubuntu on my desktop and I can't connect to my wireless router which is unprotected [well filtered by MAC addresses].

Can a kind soul help me out on what steps to do to try to solve the problem. I have tried the ndiswrapper without success, but maybe I did it wrong. I did reinstall Ubuntu after my try.

Oh, keep in mind that I don't have an Ethernet connection on my desktop ... well my router is too far away. So for installing stuff, they need to me dowloaded from my laptop.

---

### Post by Theberge43 on 2008-08-22
For info, here is my initial lshw -C network
```
theberge43@Desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:93:3a:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:6e:03:f3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by kmolnar on 2008-08-23
I have the same controller (BCM4306) and after manually getting the b43 firmware .o file and running b43-fwcutter -w /lib/firmware on it, I see my router in Network Manager, but choosing it causes the icon to oscillate its "two grey spheres with blue arrows circling" animation for quite some time before is apparently times out and returns to the "no connection" icon.

Here's my lshw -C network output:

```

katie@oasis:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:16:17:b3:9d:e0
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:62:02:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

---

### Post by OptikKnight on 2008-08-23
Hello

I'm experiencing a related problem on an HP Pavilion zd8000 laptop. On mine, however, I can't see any networks at all. Using BCM4306 rev 3.

I've investigated the problem thoroughly; from my reading, it seems the 'b43' module is still somewhat buggy, something to do with transmit power if I recall, and that the 2.6.25 and newer kernels will have better support.

Until Ubuntu upgrades the kernel, I'm feeling rather stuck. I don't want to try ndiswrapper or anything similar to use Windows drivers. I've confirmed that the firmware is up-to-date, using the proper versions of the broadcom sources and such <[http://downloads.openwrt.org/sources/]("http://downloads.openwrt.org/sources/")>, and the right version of b43-fwcutter for my kernel. Still no go...

The problem is rather widely reported, so I'm confident it will be resolved in the kernel in short order. Until then, I'm interested to know if anyone finds other good solutions.

Worth noting, however: after a series of 'rmmod' and 'modprobe' under 2.6.24-16, I got it to function normally for about 20 minutes before I rebooted again. I have not been able to reproduce that situation, despite having repeated exactly the operations listed in my BASH history. (confused.)

Good luck.

---

### Post by kmolnar on 2008-10-07
Minor update: I eventually gave up on b43 and used ndiswrapper. There's a great tutorial for this problem specifically on these forums.

The cause is apparently a signal strength problem with the b43 driver, or something like that. Something annoyingly analog. =)

---

### Post by cariboo on 2008-10-07
Did anyone read the sticky at the top of the page?

Jim

---

