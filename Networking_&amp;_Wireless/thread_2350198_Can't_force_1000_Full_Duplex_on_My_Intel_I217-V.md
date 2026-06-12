---
title: "Can't force 1000 Full Duplex on My Intel I217-V"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by arnaudlamy on 2017-01-22
Hi all, 

Here's my conf:

```

11:55 arnaud|Caladan ~ % cat /etc/issue
Ubuntu 16.04.1 LTS \n \l

lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
```

```
11:43 arnaud|Caladan ~ % dmesg | grep -e e100 -e eth0
614:[    0.701752] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
615:[    0.701753] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
628:[    0.722304] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
629:[    0.893229] e1000e 0000:00:19.0 eth0: registered PHC clock
630:[    0.893231] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) ac:22:0b:51:d7:e9
631:[    0.893232] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
632:[    0.893256] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
922:[  276.285862] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
```


When I try to force it (```
ethtool -s eth0 speed 1000 duplex full
```) even with autoneg off I've got this:

```
root@Caladan:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full
                            100baseT/Half 100baseT/Full
                            1000baseT/Full
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  1000baseT/Full
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 2
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown (auto)
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: no
root@Caladan:~#
```

```
11:54 arnaud|Caladan ~ % dmesg | grep -e e100 -e eth0
935:[ 1794.421674] e1000e 0000:00:19.0 eth0: Unsupported Speed/Duplex configuration
```

On the other side it's SAGEM box with Gigabit ports.

It's very annoying 'cause a 100Mbps connection clearly limit my server because my internet connection is more than that [IMG]https://ubuntuforums.org/images/icons/icon8.png[/IMG]

Thank you very much for your help!

---

