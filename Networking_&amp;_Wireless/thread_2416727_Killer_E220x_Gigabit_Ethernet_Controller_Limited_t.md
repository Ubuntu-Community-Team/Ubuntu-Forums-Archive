---
title: "Killer E220x Gigabit Ethernet Controller Limited to 100mbps"
date: 2019-04-14
forum: Networking &amp; Wireless
---

### Post by jonowarren on 2019-04-14
Hello,

Decided to make the switch to ubuntu from win 8. All going well so far, except for the fact that my ethernet seems to be limited to 100mbps.

Running:
```
lshw -c network
```

outputs:
```
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 13
       serial: d8:cb:8a:34:c5:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:f7300000-f733ffff ioport:d000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

Not really sure where to start, tried googling but not really finding anything useful.

EDIT: Apparently I am a dumbass, my switch is only 100mps, ordered a new one!

---

### Post by praseodym on 2019-04-14
Check not only the switch, but also all other components, like cable, etc

---

