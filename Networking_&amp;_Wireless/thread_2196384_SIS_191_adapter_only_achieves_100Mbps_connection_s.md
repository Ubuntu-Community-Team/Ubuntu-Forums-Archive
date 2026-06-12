---
title: "SIS 191 adapter only achieves 100Mbps connection speed"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by hazica on 2013-12-29
Hi everyone using Kubuntu 13.10 with linux 3.11.04. My NIC is a SIS 191 Gigabit Ethernet Adapter and it fails to connect at 1 Gbps to my router. 

Some technical information: 

lshw -C network
```
description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: 02
       serial: 00:22:15:91:0c:c5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=full ip=192.168.178.24 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 memory:fddfcc00-fddfcc7f ioport:cc00(size=128)

```

and ethtool eth1 says:

```
Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000037 (55)
                               drv probe link ifdown ifup
        Link detected: yes

```

The Network-Manager applets of both kde and gnome also tell me that I have a 100Mbit/s connection.

This seems to be consistently showing that the card can only handle 100Mbit/s, even though it should handle up to 1Gbit/s according to the manufacturer's specs.

But here is where things start behaving somewhat oddly:
My router ( Fritz Box) shows the adapter as being connected at 1Gbit/s.
And here is the output of 

dmesg | grep sis19

```
[    1.268690] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.268927] sis190 0000:00:04.0: setting latency timer to 64
[    1.268957] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.268959] sis190: 0000:00:04.0: Error EEPROM read 0
[    1.268962] sis190: 0000:00:04.0: Read MAC address from APC
[    1.324026] sis190: 0000:00:04.0: Atheros PHY transceiver at address 1
[    1.820032] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.852227] sis190 0000:00:04.0 eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at ffffc90000642c00 (IRQ: 19), 00:22:15:91:0c:c5
[    1.852231] sis190 0000:00:04.0 eth0: RGMII mode.
[    1.852237] sis190 0000:00:04.0 eth0: Enabling Auto-negotiation
[   40.608035] sis190 0000:00:04.0 eth1: mii ext = 0000
[   40.636026] sis190 0000:00:04.0 eth1: mii lpa=cde1 adv=01e1 exp=000f
[   40.656030] sis190 0000:00:04.0 eth1: link on 1000 Mbps Full Duplex mode
[  281.976035] sis190 0000:00:04.0 eth1: auto-negotiating...
[  287.092052] sis190 0000:00:04.0 eth1: mii ext = 0000
[  287.116037] sis190 0000:00:04.0 eth1: mii lpa=cde1 adv=01e1 exp=000f
[  287.132039] sis190 0000:00:04.0** eth1: link on 1000 Mbps Full Duplex mode**

```

Isn't this weird?

Is there any way I can get the full 1Gbps connection speed? Googling did not yield any solutions. 
Thanks

---

