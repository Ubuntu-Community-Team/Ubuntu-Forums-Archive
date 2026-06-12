---
title: "ethtool , wakeonlan - not working ."
date: 2022-11-08
forum: Networking &amp; Wireless
---

### Post by dorian-ionescu on 2022-11-08
The configuration is simple:
Rooter - Link to my computer (windows 10 with WSL2 - upgraded yesterday)      192.168.1.15/24 - static address
Rooter - switch 1 - switch 2 - Server(ubuntu server 22.04 - upgraded today)       192.168.1.250/24 -static address
**_*The BIOS setting to wake on lan for server is active.*_**

**lscpi -tv**
```
-[0000:00]-+-00.0  Intel Corporation 4th Gen Core Processor DRAM Controller
           +-01.0-[01]--+-00.0  NVIDIA Corporation GM206 [GeForce GTX 960]
           |            \-00.1  NVIDIA Corporation GM206 High Definition Audio Controller
           +-14.0  Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
           +-16.0  Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
           +-1a.0  Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
           +-1b.0  Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
           +-1c.0-[02]--
           +-1c.2-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           +-1c.3-[04-05]----00.0-[05]--
           +-1d.0  Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
           +-1f.0  Intel Corporation B85 Express LPC Controller
           +-1f.2  Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
           \-1f.3  Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller

```

I used **sudo ethtool -s enp3s0 wol g** to change state of Wake-On but it changes back to **d **after restart.
```

Settings for enp3s0:
        Supported ports: [ TP    MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: Symmetric Receive-only
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
        Auto-negotiation: on
        master-slave cfg: preferred slave
        master-slave status: slave
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: external
        MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: d
        Link detected: yes
```
 
**sudo ethtool -s enp3s0 wol g**
**sudo ethtool enp3s0**

```
Settings for enp3s0:
        Supported ports: [ TP    MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: Symmetric Receive-only
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
        Auto-negotiation: on
        master-slave cfg: preferred slave
        master-slave status: slave
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: external
        MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: g - **THIS CHANGES TO d after restart**
        Link detected: yes

```

i edited [B]/lib/systemd/network/99-default.link

[/B]```
[Match]OriginalName=*
MACAddress=2c:56:dc:3c:26:c4

[Link]
NamePolicy=keep kernel database onboard slot path
AlternativeNamesPolicy=database onboard slot path
MACAddressPolicy=persistentWakeOnLan=magic
```
I am out of ideas,
Can anyone help?
Thank you.

---

