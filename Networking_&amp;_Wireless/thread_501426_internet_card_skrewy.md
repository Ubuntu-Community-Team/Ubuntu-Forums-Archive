---
title: "internet card skrewy"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by -=Viper=- on 2007-07-15
Ok well i have a BCM4318 and it keeps droping the connection (like i cant surf the web or get updates) but it says that i am connected -_-"  I can not figure out why.  I did an install of the driver that i was given like 2 weeks ago (i just reinstalled ubuntu for like the 12 time this week just so the wireless would work in the 32 bit and this is the farthest  i have gotten.  Can soneone tell me why it keeps dieing

---

### Post by fredj on 2007-07-16
Certain wireless card/router combinations often seem to drop the connection when the network manager 
is used.
This also happens in Windows XP but windows reconnects again quickly. You may have to configure your
network manually. Open a terminal and post the output of 'lshw -class network'. Also what sort of network
encryption are you using WEP or WPA?

---

### Post by -=Viper=- on 2007-07-17
> **fredj said:**
> Certain wireless card/router combinations often seem to drop the connection when the network manager 
is used.
This also happens in Windows XP but windows reconnects again quickly. You may have to configure your
network manually. Open a terminal and post the output of 'lshw -class network'. Also what sort of network
encryption are you using WEP or WPA?

I am using WPA and here is the code

```
ernesto@ernesto-laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@03:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:20:04:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic ip=192.168.1.116 latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d4204000-d4205fff irq:21
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:35:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:d420a400-d420a4ff irq:20
ernesto@ernesto-laptop:~$ 

```

---

