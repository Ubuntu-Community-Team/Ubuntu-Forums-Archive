---
title: "problem with wireless card"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by altonis on 2009-12-30
Hello, i am completely new to Ubuntu and i just installed it on used laptop. 

The problem is that i can't even detect wireless network - it shows that "Device is not ready"

I typed 

lshw -C network 
And this is what i get.

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:9b:a3:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:5 ioport:3000(size=256) memory:e0209800-e02098ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:10 memory:e0204000-e0205fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:38:d3:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Could you please help me? Actually it looks like the wireless adapter is just switched off, but i can't turn it on.

---

### Post by Dude-PWB- on 2009-12-30
You need to search for the drivers/solutions for your wireless device. It is a very common device in the networking forums.

Here is your device, as it is listed in your output. 

```
BCM4318
```

---

### Post by Onimishra on 2009-12-30
Welcome to Ubuntu, and the wonderfull world of Broadcom problems :)

To get ur network card working, first open a terminal at write

sudo apt-get update

When it's done and you've restarted (if nessesary) go to restricted drivers in Setting.
There should be one called STA. That's the driver Braodcom provide for ubuntu users.

---

### Post by altonis on 2009-12-31
Thank you, i did all of this and enabled Broadcom driver. 

However, "Wireless is disabled". Maybe there is a problem with the wireless device?

---

### Post by redbook4574 on 2010-04-03
> **altonis said:**
> Thank you, i did all of this and enabled Broadcom driver. 

However, "Wireless is disabled". Maybe there is a problem with the wireless device?

Try sudo apt-get install bcmwl-kernel-source

---

