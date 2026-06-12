---
title: "Wireless not working"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Lilszamora on 2008-06-22
Ok I I tried the guide here:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
and it didn't work...It worked the last time I tried it but I upgraded to the 64-bit architecture and now it doesn't...someone help me please!

---

### Post by Lilszamora on 2008-06-22
ok here's the info I get with the lshw -C network in the terminal if it helps

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:5b:b1:dd
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=10.0.0.4 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

someone please help I love ubuntu but I can't use it if I keep on having to use my wired connection, it defeats the purpose of my labtop

---

