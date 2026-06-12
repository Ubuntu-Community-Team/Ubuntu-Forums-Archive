---
title: "Install Linksys EG1032"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2008-09-13
I have spent hours on this. I have googled a number of times and can't find a solution. I am running Mythbuntu Hardy. I have a EG1032 and am trying to connect to a Linksys WRT610N. I have a green light on the router which should indicate a gigabit connection. Everything seems to work fine in the GUI setup. I am assigning a static IP of 192.168.1.119, 255.255.255.0 and GW of 192.168.1.1. When I also have the onboard NIC running, I can ping, SSH and remote desktop to 119 as if it is working. However, when I disable the onboard NIC, I can even ping my GW address.

lspci says:

00:0a.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 12)

ifconfig says:

eth2      Link encap:Ethernet  HWaddr 00:12:17:54:d5:74  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

dmesg tail says:

[  146.263297] skge eth2: disabling interface
[  165.454738] skge eth2: enabling interface
[  165.462349] ADDRCONF(NETDEV_UP): eth2: link is not ready

Any assistance is appreciated. This is my first GIG-E device. Thanks.

---

### Post by lingenfr on 2008-09-14
I guess this has the Marvell Yukon, so I am looking at that thread as well. Here is some additional information.

$ sudo ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x00000037 (55)
        Link detected: no

$ sudo ethtool -i eth2
driver: skge
version: 1.13
firmware-version: N/A
bus-info: 0000:00:0a.0

---

### Post by lingenfr on 2008-10-18
To provide further clarification, this is a v2 card. There is information on the web, mainly about v3, but some v2. However, the newest is several years and several kernels old. I just want to make sure I am applying the right fix. It looks like I am talking to myself, but just in case I thought I would provide the additional information.

---

### Post by lingenfr on 2008-10-26
Come on, help a brother out.

---

### Post by lingenfr on 2008-11-08
Bump. Still need help.

---

### Post by lingenfr on 2008-11-10
Bump.

---

### Post by lingenfr on 2008-11-11
Bump bump.

---

### Post by lingenfr on 2008-11-15
Bump bump bump.

---

### Post by lingenfr on 2008-11-17
Bump bump bump bump.

---

### Post by lingenfr on 2008-11-30
Bump bump bump bump bump.

---

### Post by lingenfr on 2008-12-12
Bump bump bump bump bump bump.

---

