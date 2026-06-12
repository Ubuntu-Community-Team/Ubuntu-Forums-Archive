---
title: "Wake-on-LAN troubles"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by morlock81 on 2008-08-11
Hi there!

I didn't find a solution for my problem in the existing threads, so I figured somebody might have an idea.

Here's the situation: My PC has multiple hard drives. One is running Ubuntu (Hardy), one is running XP.

When I boot XP and shut down, the PC will wake on magic packets, but when I run Hardy it won't. It used to work on Gutsy, but after I upgraded I also installed VirtualBox and added a virtual network device, so I don't know if the upgrade or the virtual device is causing the problem...
The NIC is set to wake on magic packets (of course, as it wakes when XP was the last OS used), so no problems there.

I'll post the output of ethtool and ifconfig, maybe that helps:

```
    
root@inhouse-server:/home/morlock# ethtool eth1
    Settings for eth1:
       Supported ports: [ MII ]
       Supported link modes:   10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Full
       Supports auto-negotiation: Yes
       Advertised link modes:  10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Full
       Advertised auto-negotiation: Yes
       Speed: 100Mb/s
       Duplex: Full
       Port: MII
       PHYAD: 1
       Transceiver: external
       Auto-negotiation: on
       Supports Wake-on: g
       Wake-on: g
       Link detected: yes

    root@inhouse-server:/home/morlock# ethtool tap0
    Settings for tap0:
       Supported ports: [ ]
       Supported link modes:   
       Supports auto-negotiation: No
       Advertised link modes:  Not reported
       Advertised auto-negotiation: No
       Speed: 10Mb/s
       Duplex: Full
       Port: Twisted Pair
       PHYAD: 0
       Transceiver: internal
       Auto-negotiation: off
       Current message level: 0xffffffa1 (-95)
       Link detected: no

    root@inhouse-server:/home/morlock# ethtool vbox_bridge
    Settings for vbox_bridge:
       Link detected: yes

    root@inhouse-server:/home/morlock# ifconfig eth1
    eth1      Link encap:Ethernet  Hardware Adresse 00:1e:8c:46:91:c5 
              inet6-Adresse: fe80::21e:8cff:fe46:91c5/64 Gltigkeitsbereich:Verbindung
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
              RX packets:1947908 errors:0 dropped:0 overruns:0 frame:0
              TX packets:3113768 errors:0 dropped:0 overruns:0 carrier:0
              Kollisionen:0 Sendewarteschlangenlnge:1000
              RX bytes:123761658 (118.0 MB)  TX bytes:3775866146 (3.5 GB)
              Interrupt:222 Basisadresse:0xe000

    root@inhouse-server:/home/morlock# ifconfig tap0
    tap0      Link encap:Ethernet  Hardware Adresse 00:ff:1f:00:2e:2b 
              inet6-Adresse: fe80::2ff:1fff:fe00:2e2b/64 Gltigkeitsbereich:Verbindung
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:3876 overruns:0 carrier:0
              Kollisionen:0 Sendewarteschlangenlnge:500
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

    root@inhouse-server:/home/morlock# ifconfig vbox_bridge
    vbox_bridge Link encap:Ethernet  Hardware Adresse 00:1e:8c:46:91:c5 
              inet Adresse:192.168.1.101  Bcast:192.168.1.255  Maske:255.255.255.0
              inet6-Adresse: fe80::21e:8cff:fe46:91c5/64 Gltigkeitsbereich:Verbindung
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
              RX packets:1967573 errors:0 dropped:0 overruns:0 frame:0
              TX packets:3149263 errors:0 dropped:0 overruns:0 carrier:0
              Kollisionen:0 Sendewarteschlangenlnge:0
              RX bytes:94494088 (90.1 MB)  TX bytes:3814072470 (3.5 GB)


```
Ideas anyone? I would be really glad if I got this working again.

Kind regards,
morlock

---

### Post by morlock81 on 2008-08-21
I'm sorry for pushing this topic, but I'm really lost here. No ideas anyone?

---

