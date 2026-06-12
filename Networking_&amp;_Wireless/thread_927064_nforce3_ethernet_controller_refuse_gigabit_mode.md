---
title: "nforce3 ethernet controller refuse gigabit mode"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by nduboc on 2008-09-22
Hi,

 My nforce3 ethernet controller (on an Asustek K8n-E motherboard) correctly runs in 100Base-T mode but refuse 1000Base-T mode. Cable is cat5e and the switch is 1000Base-T capable. If I connect another machine to the same switch port, using the same cable, it connects in 1000Base-T mode and I obtain transfer rates at 20 or 30MBytes/s.

 1000Base-T is not even advertised by ethtool as a supported mode. But this controller is supposed to support this mode.

 I'm running Ubuntu 8.04 with kernel 2.6.24-19-generic.

 Does someone have an idea why I can't get 1000Base-T ?
 Did someone with the same configuration manage to get that mode working ?

Details:

```

$ sudo lspci -vd  10de:00df
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N-E
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: [44] Power Management version 2

```

```

$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```

```

$ dmesg|egrep "eth0|forcedeth"
[   24.899426] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   25.418040] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x90c3 @ 1, addr 00:11:d8:63:74:4a
[   25.418046] forcedeth 0000:00:05.0: csum timirq lnktim desc-v2
[  127.835134] eth0: no IPv6 routers present

```

---

### Post by nduboc on 2008-09-26
OK, forget about it.

It seems that some nforce3 chipsets (nforce3 250GB) are gigabit capable and others aren't. Mine is a simple nforce3 250.

Sorry for the noise,

-- 
Nicolas

---

