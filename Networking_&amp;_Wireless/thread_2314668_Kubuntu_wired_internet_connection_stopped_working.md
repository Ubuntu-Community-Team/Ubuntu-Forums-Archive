---
title: "Kubuntu wired internet connection stopped working"
date: 2016-02-22
forum: Networking &amp; Wireless
---

### Post by ben135 on 2016-02-22
My internet was working fine for a long time, been having router troubles, and all of a sudden today my internet doesn't work. I assume the router died so I just hardline straight into the wall. No internet. I was doing some stuff trying to fix it and I deleted the Netgear connection via the connection editor. Now the connection indicator has a question mark over it. 

output for sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes


output for sudo lshw -C Network

  *-network              
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 14:da:e9:03:ea:47
       size: 100Mbit/s
       capacity: 1Gbit/s                                                                                     
       width: 64 bits                                                                                         
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.18 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:79 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff

 If you need anything else, let me know. Thanks!

---

### Post by ben135 on 2016-02-23
anyone?

---

