---
title: "Can't connect to wired ethernet on Ubuntu 14.04.1"
date: 2014-09-08
forum: Networking &amp; Wireless
---

### Post by nick142 on 2014-09-08
Hello,

I'm having some problems connecting to the Internet from my Ubuntu 14.04.1 install.  I've turned off Wi-Fi just to see if I can get a wired connection going.  So far the connection attempts to the wired Internet keep failing, resulting in the message "Disconnected - you are now offline" appearing.

I've seen a lot of these types of request for help in the forums, so I was hoping someone could help me step through it.  The most recent post I saw asked for output from some commands, so I'll post them here in hopes of getting the troubleshooting started:

```
sudo lshw -C network
[sudo] password for nick:
  *-network DISABLED
          description: Wireless interface
          product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
          vendor: Intel Corporation
          physical id: 0
          bus info: pci@0000:0b:00.0
          logical name: wlan0
          version: 61
          serial: 00:1f:3b:40:95:e5
          width: 64 bits
          clock: 33 MHz
          capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=iwl4965 driverversion=3.13.0-32-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
          resources: irq:49 memory:fc500000-fc501fff
  *-network
          description: Ethernet interface
          product: 88E8055 PCI-E Gigabit Ethernet Controller
          vendor: Marvell Technology Group Ltd.
          physical id: 0
          bus info: pci@0000:0d:00.0
          logical name: eth0
          version: 13
          serial: 00:0b:97:53:30:b7
          size: 100Mbit/s
          capacity : 1 Gbit/s
          width: 64 bits
          clock: 33 MHz
          capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
          resources: irq:45 memory:fc600000-fc603fff ioport:4000(size=256) memory:44a00000-44a1ffff
```

```
sudo ethtool eth0
Settings for eth0
Supported ports: [ TP ]
Supported link modes:  10baseT/Half 10baseT/Full
                                   100baseT/Half 100baseT/Full
                                   1000baseT/Half 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes:  10baseT/Half 10baseT/Full
                                   100baseT/Half 100baseT/Full
                                   1000baseT/Half 1000baseT/Full
Advertised pause frame use: No
Advertised auto-negotiation: No
Speed: 100 Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: pg
Wake-on: g
Current message level: 0x000000ff (255)
                                  drv probe link timer ifdown ifup rx_err tx_err
Link detected: yes
```

Your help much appreciated in advanced.  Thanks.

---

### Post by nick142 on 2014-09-08
I should also mention that running Ubuntu from the DVD results in a perfectly find wired Internet connection.  I don't know why there would be a difference.

---

