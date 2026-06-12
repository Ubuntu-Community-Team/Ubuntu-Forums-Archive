---
title: "Low network bandwidth (4Mbit/s)!"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Ringwraith82 on 2008-06-21
Hello friends of Ubuntu ;)

Accessing my Ubuntu(Hardy Heron 2.6.24-19) box from a WinXP-machine via network(wired) is very slow. 
Copying files from Ubuntu to Windows => 300KB/s (SAMBA or SFTP)

Since I switched from Dapper to Hardy I am noticing weird performance issues. And i think they are changing from kernel-update to kernel-update. :roll:

Can someone help me hunting down this bottleneck, please?
If you need more information please tell me what you need and how to get it. ;) Thanks.

One more thing: I can't replace the NIC which would be the simplest solution. The box is a notebook and therefore I have to find another solution for this mess.


Output of iperf:
```

Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.120 port 5001 connected with 192.168.1.101 port 1620
[  4]  0.0-10.0 sec  4.70 MBytes  3.94 Mbits/sec

```

lspci:
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 11)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 80)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 01)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:08.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:08.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 11)
02:00.0 USB Controller: NEC Corporation USB (rev 41)
02:00.1 USB Controller: NEC Corporation USB (rev 41)
02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

```

mii-tool
```

eth0: negotiated 100baseTx-FD, link ok

```

ethtool
```

Settings for eth0:
        Supported ports: [ TP MII ]
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
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: yes

```

---

