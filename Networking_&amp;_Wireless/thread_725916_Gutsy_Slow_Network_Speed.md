---
title: "Gutsy Slow Network Speed"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by zaffod on 2008-03-16
I am experiencing very slow internet speeds from my Gusty machine (10kb). The XP machine on my LAN is normal (300kb). 

Measuring this from online speed tests, but also noting download rates from Update Manager. Updates are coming down much slower than usual.  

Problem started when I upgraded my internet router to a cisco 837. For some reason, Ubuntu won't play nice with it, but the Windows machine is fine. 

SMB transfers between the two machines "seem" ok. 1gb file in minutes. 

I have connected Gutsy to the same cable used as the XP machine to rule out cable issues. I have disable ipv6 in firefox and in /etc/modprobe.d/aliases. I have also assigned the XP ip address to the Ubuntu machine to rule out any router config issue.


here's output for ```
ethtool eth0
```
Settings for eth0:
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
        Wake-on: d
        Link detected: yes

Here's output from ```
lshw:
```
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:18:f3:8a:3b:25
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.0.11 latency=0 link=yes 
maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
 
Any help would be** much appreciated! **Otherwise I may have to try another distro. Too many things going bad since Gutsy and no one seems to be fixing them.

---

### Post by zaffod on 2008-03-17
An IOS upgrade on the new dsl modem appears to have fixed my problem.
I guess something in the Ubuntu IP stack must be different to the Windows IP stack as only my Linux machine was impacted by older software on the modem.

---

