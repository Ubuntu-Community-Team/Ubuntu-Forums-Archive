---
title: "HP dv6000 Laptop Intel Pro/Wireless 3945 ABG Problems"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by mand0 on 2007-04-09
My brand new dv6000 is having some serious trouble with it's wireless.  To clarify, it has the the ipw 3945 driver, not the Broadcom one.

The wireless seems to work sporadically.  I installed Ubuntu 7.04 Beta, downloaded all the updates, and the wireless card was detected.  I brought the laptop to a cafe to test it out and it was able to pick up the wifi connections with no problem.  The next day I take my laptop to a library and all of a sudden the wireless card disappeared.


Typing:

```
iwconfig
```

Gives me:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

When I know for a fact there is a eth1! It was working the day before!

Typing:

```
sudo lshw -class network
```

Gives me:

```
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d8000000-d8000fff irq:16
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 00
       serial: 00:1b:24:13:37:47
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:da000000-da01ffff ioport:4000-401f irq:18
```

Ubuntu recognizes the card, as shown above.  I have the linux-restricted-modules installed.  I am starting to think this is a [hardware]("http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1104931") problem.  Has anyone here had this problem? Should I contact HP?

---

### Post by mand0 on 2007-04-09
Wow... I think I just figured it out. There's a switch on the front of the laptop I need to turn in order for the wireless to work...

---

### Post by meonline2 on 2007-09-06
Even with the switch on, it does not work for me.  I am using Open suse 10.2 with GNOME.

---

