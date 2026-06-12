---
title: "Cannot get 12.04LTS to WOL"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by gary47 on 2014-09-24
I have the ROM set, I have the Net Card set for g but cannot get it to Wake.. I changed drivers from r8169 to r8168 but still no luck

sudo lshw -C network   Gives you

 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:4d:fa:d3
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.039.00-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 ioport:e800(size=256) memory:febff000-febfffff memory:f8ff0000-f8ffffff memory:febc0000-febdffff

sudo ethtool eth0   Gives you

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

sudo lspci -v

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
	Subsystem: Dell Device 02ac
	Physical Slot: 0-2
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f8ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-e0-4c-68-00-00-00-03
	Kernel driver in use: r8168
	Kernel modules: r8168



Anybody have any clues what I am doing wrong?? I am new to Ubuntu and really don't know where to go from here...

---

### Post by TheFu on 2014-09-24
I always have to send 2 WOL packets - usually 3-5 sec apart for the WOL to work here. Plus, WOL doesn't work across subnets.

---

### Post by weatherman2 on 2014-09-24
Gary, how are you trying to wake up the Ubuntu machine?  How are you sending the magic packets over the network?  To wake up using another Linux machine, I use the "wakeonlan" command (easy to install):

```

wakeonlan -i 192.168.1.255 00:11:22:33:44:55

```

(Replace "192.168.1.255" with your own subnet; replace "00:11:22:33:44:55" with the MAC/hardware address of the network card on the machine you are trying to wake up.)



I occasionally need to send the magic packet twice for WOL to work but very rarely.  Most of the time, I can send one magic packet to get WOL to work.  I use WOL on several different machines with Ubuntu 12.04 or 14.04.  A few of them use the r8169 (or r8168) driver.

Make sure WOL is enabled in the BIOS too.

---

