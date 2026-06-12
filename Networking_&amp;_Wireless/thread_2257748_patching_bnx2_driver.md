---
title: "patching bnx2 driver"
date: 2014-12-22
forum: Networking &amp; Wireless
---

### Post by Meraman on 2014-12-22
I have ubuntu server: ```
uname -a
```:

Linux DaVinci003 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I have eth1 NIC: ```
ethtool -i eth1
```:

driver: bnx2
version: 2.2.1
firmware-version: 7.4.8 bc 7.4.0 NCSI 2.0.11
bus-info: 0000:02:00.1
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes

```
ethtool eth1
``` shows:

Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes




```

lspci -i
``` command shows:

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet (rev 20)
        Subsystem: Dell Device 04dd
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c0000000 (64-bit, non-prefetchable) [size=32M]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+
        Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-
        Capabilities: [ac] Express Endpoint, MSI 00
        Capabilities: [100] Device Serial Number d4-ae-52-ff-fe-d1-4f-1c
        Capabilities: [110] Advanced Error Reporting
        Capabilities: [150] Power Budgeting <?>
        Capabilities: [160] Virtual Channel
        Kernel driver in use: bnx2
        Kernel modules: bnx2


02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet (rev 20)
        Subsystem: Dell Device 04dd
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at c2000000 (64-bit, non-prefetchable) [size=32M]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+
        Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-
        Capabilities: [ac] Express Endpoint, MSI 00
        Capabilities: [100] Device Serial Number d4-ae-52-ff-fe-d1-4f-1d
        Capabilities: [110] Advanced Error Reporting
        Capabilities: [150] Power Budgeting <?>
        Capabilities: [160] Virtual Channel
        Kernel driver in use: bnx2
        Kernel modules: bnx2



I am transmitting around 100 Mbps UDP multicasts from this eth1 interface.

My problem is, after sometime (few hours) UDP multicasts has been started, the packets started loosing. I confirmed same packet losses at different receivers, so its from eth1 sender interface only. The problem gets worst with time.

```
ethtool -g eth1
``` command shows:

Ring parameters for eth1:
Pre-set maximums:
RX:             2040
RX Mini:        0
RX Jumbo:       8160
TX:             255
Current hardware settings:
RX:             255
RX Mini:        0
RX Jumbo:       0
TX:             255

I guess packet losses has to do something with small TX ring size (255). I can't increase TX further, because thats maximum.

Reading this: [http://serverfault.com/questions/637600/how-do-i-increase-the-ring-parameters-for-a-nic-on-a-linux-server?rq=1](http://serverfault.com/questions/637600/how-do-i-increase-the-ring-parameters-for-a-nic-on-a-linux-server?rq=1) shows how to increase TX maximum ring size, but I dont know how to apply this patch. Can anybody please help me.

---

