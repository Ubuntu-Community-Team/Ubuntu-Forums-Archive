---
title: "Wireless connection drops - card disappears"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by MikkelEDB on 2007-11-24
This problem has been haunting me for days now and I am not sure what to make of it.

The problem: My wireless connection drops after 20-60 minutes of use and it cannot reconnect. After a reboot iwconfig no longer shows a wireless card is even present, it's gone missing.

I have only tried switching network manager to wicd but it will still just disappear. If I turn the computer off for 30+ minutes or so, I can boot and everything works fine untill it drops again and the card is "gone".

Ok, right now I am connected through my wireless card on this notebook that has the issue and here is  a printout while it's working.

```

[sudo] password for ejer:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:57:84:c4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:00:61:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.38 multicast=yes wireless=IEEE 802.11g

```

When it disconnects, before next reboot, it will say the same exept -network - DISABLED. Of course then after immediate reboot or just a few minutes after it will say nothing.

Why does my card disappear? 

This is my first attempt with a linux distro so I am not knowledable about it, I fresh out of winxp where everything was working fine (why switch then, hehe). Anyways, I know like me you will probably think hardware failure but as it was working always to the same day that I formatted my xp install with ubuntu 7.10 I really don't think so but I don't know for sure of course.

If anyone has ANY similar experience I sure would appreciate to hear from you. Thank you very much. :)

---

### Post by maldek on 2007-11-24
Right now I just experienced the exact same thing.  I'm using 7.10 on my Dell E1505 I bought over the summer when Dell first released their Ubuntu line.  Wireless has worked fine up until now.

If someone has an idea what's causing this, please let us know. I have a research paper to write.

---

### Post by maldek on 2007-11-24
Bump.

I really, really need help with this.

---

### Post by MikkelEDB on 2007-11-25
Is your card also Realtek, I am interested in knowing if this happens to other card types.

---

