---
title: "Wireless not working"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Lilszamora on 2008-07-14
ok i entered the
```
 lshw -C network
```

and I get
```
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
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=10.0.0.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
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

can someone please help me, I love ubuntu but I just can't seem to get it to work

---

### Post by jingo811 on 2008-07-15
Is your Wireless device listed on this list?
[http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom](http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom)

---

