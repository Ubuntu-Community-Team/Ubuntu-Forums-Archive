---
title: "Wired network problems with 'skge' eth embeded"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by aim on 2007-12-03
*x86 version of Ubuntu 7.10 on amd64 system*

**lspci -vvvv**
```

00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (5750ns min, 7750ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at fb800000 (32-bit, non-prefetchable) [size=16K]
        Region 1: I/O ports at 9800 [size=256]
        Expansion ROM at fb700000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data

```

**ethtool eth0**
```

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x00000037 (55)
        Link detected: yes

```
[B]
dmesg[/B]
```

[  100.936000] martian source 89.223.41.19 from 0.0.0.0, on dev eth0
[  100.936000] ll header: 00:13:d4:d6:42:8f:00:1a:e2:39:5d:c9:08:00
<skipped many lines of the same problem>
[10764.988000] NETDEV WATCHDOG: eth0: transmit timed out
[10864.988000] NETDEV WATCHDOG: eth0: transmit timed out
[10959.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11059.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11159.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11254.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11349.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11454.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11549.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11644.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11749.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11844.988000] NETDEV WATCHDOG: eth0: transmit timed out
[11944.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12044.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12139.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12239.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12339.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12434.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12534.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12629.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12724.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12829.988000] NETDEV WATCHDOG: eth0: transmit timed out
[12924.988000] NETDEV WATCHDOG: eth0: transmit timed out
[13024.988000] NETDEV WATCHDOG: eth0: transmit timed out

```
**reboot**


How can I deal with this?!

---

