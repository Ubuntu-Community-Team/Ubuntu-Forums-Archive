---
title: "No wireless connection Ubuntu's latest LTS version"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by liran2 on 2015-04-10
Hi! 
I'm really hoping you guys will help me in solving this since it's setting me back on my Python studying program I made myself.
I've tried using wired connection but now I don't the option to get a wired connection (like 0 chance).

I've got an acer E1572G running windows 64bit and using a qualcomm atheros 956x.

here's an lshw -C network
(oh and I removed the serial myself, it was in the output)
```
  *-network:0                    description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: -
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI latency=0 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:19 memory:fd5c0000-fd5dffff memory:fdff0000-fdffffff ioport:2000(size=64) memory:fd500000-fd50ffff
  *-network:1
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 01
       serial: -
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI latency=0 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:16 memory:fd520000-fd53ffff memory:fd540000-fd54ffff ioport:20a0(size=8) memory:fd550000-fd55ffff



```

I tried using rfkill list all to see if there's anything blocked and ran rfkill unblock all (got nothing on both of those)
what is list to do?

---

