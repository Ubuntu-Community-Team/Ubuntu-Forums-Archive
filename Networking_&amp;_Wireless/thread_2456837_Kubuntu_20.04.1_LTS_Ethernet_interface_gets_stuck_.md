---
title: "Kubuntu 20.04.1 LTS: Ethernet interface gets stuck after inactivity period"
date: 2021-01-20
forum: Networking &amp; Wireless
---

### Post by nicolasduminil on 2021-01-20
I'm using Kubuntu 20.04 LTS on a DELL XPS 13 9360 connecting to the  network via a DELL WD15 docking station. After several minutes of  inactivity the Ethernet interface goes stalled and no any internet  connection or LAN works. Trying to disconnect and reconnect doesn't work  'cause, once stalled, it is not able to take the DHCP address.  Sometimes it even behaves like if the network cable is disconnected. The  only thing I can do it to reboot. I change the network cable (CAT 5),  the RJ45 plug, but nothing else works.

 Here is the topology:
 Router -> CAT 5 cable -> Switch -> CAT 5 Cable -> RJ45  plug -> DELL WD 15 docking station -> USB-C -> Computer.
 Having tried the following topology:
 Router -> CAT 5 cable -> RJ45 plug -> DELL WD 15 docking station -> USB-C -> Computer doesn't change anything.
 Here are some information:

[FONT=monospace]00:02.0 [COLOR=#ff5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: Intel Corporation Iris Plus Graphics 640 (rev 06) [/COLOR]
        DeviceName:  Onboard IGD 
        Subsystem: Dell Iris Plus Graphics 640 

[/FONT]
 *-network:2
   description: Ethernet interface
   physical id: 4
   bus info: usb@4:1.2
   logical name: enxa44cc8b16f57
   serial: a4:4c:c8:b1:6f:57
   size: 1Gbit/s
   capacity: 1Gbit/s
   capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.11 duplex=full ip=192.168.1.15 link=yes multicast=yes port=MII speed=1Gbit/s

Settings for enxa44cc8b16f57:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00007fff (32767)
 drv probe link timer ifdown ifup rx_err tx_err tx_queued intr tx_done rx_status pktdata hw wol
    Link detected: yes
 
Even stranger, I have a DELL XPS 15 9570 box as well, running the  same Kubuntu release (20.04.1 LTS) on the same network, using the same  DELL WD 15 docking station, with exactly the same topology, which  doesn't show the issue.
 Here are the same information for the DELL XPS 15:

 *-network:0
   description: Ethernet interface
   physical id: 2
   bus info: usb@4:1.2
   logical name: enxe4b97acb30ee
   serial: e4:b9:7a:cb:30:ee
   size: 100Mbit/s
   capacity: 1Gbit/s
   capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.11 duplex=full ip=192.168.1.47 link=yes multicast=yes port=MII speed=100Mbit/s

Settings for enxe4b97acb30ee:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00007fff (32767)
                           drv probe link timer ifdown ifup rx_err tx_err tx_queued intr tx_done rx_status pktdata hw wol
    Link detected: yes
 
The only difference I can see is that my DELL XPS 15 connects at  100Mbit/s, while the XPS13 connects at 1Gbit/s. I'm not sure where from  this difference comes from but I have configured the Network Manager on  the XPS 13 such that to have the Link Negotiation "manual" instead of  "automatic" or "ignore" and to force it at 100Mbit/s but, besides the  fact the interface is much slower, nothing has changed, the issue is  still present.
 The issue didn't happen previously before migrating from 18.04 LTS to  20.04 LTS. I would think that it's a 20.04 LTS issue but I have two  boxes running the same release and only one has the issue. The two boxes  are running the same kernel version which is Ubuntu 20.04.1 LTS.
 Could someone help me here please ?
 Many thanks in advance.
 Kind regards,
 Seymour

---

### Post by howefield on 2021-01-20
Thread moved to the "*Networking & Wireless*" forum, a better fit than the non support forum that you posted to.

---

