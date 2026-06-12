---
title: "slow upload speeds from gateway computer, but not from LAN"
date: 2022-10-13
forum: Networking &amp; Wireless
---

### Post by brazzmonkey on 2022-10-13
Hi there,
I run Ubuntu server as a gateway between my LAN and Internet.
General setup is as follows:
internet <-- optic fiber 10G Down / 1G Up --> internet provider box <-- SFP+ 10G --> gateway <-- ethernet 1G (x2, bridged) --> LAN

Download speed from the internet is fine (internet -> gateway, internet -(gateway)-> LAN). I get several GBps to gateway, and 1 GBps to LAN, as expected.
Upload speed from LAN is fine (LAN ->gateway, LAN -(gateway)-> internet). I get 1 GBps for both, which is expected as well.
But upload speed from gateway to the internet is surprising low (gateway -> internet). I only get 0.2 to 0.3 Gbps.

Would anyone have an idea about why I get such low upload speed from the gateway, but not from LAN?

Speed tests from/to the internet were done with Ookla speedtest (command line).
Speed tests between LAN and gateway were done using iperf, among others.
Results are consistent and reproducible.

enp1s0 is the 10G NIC (Intel-based)
```
$ sudo ethtool enp1s0
Settings for enp1s0:
        Supported ports: [ FIBRE ]
        Supported link modes:   10000baseT/Full
        Supported pause frame use: Symmetric
        Supports auto-negotiation: No
        Supported FEC modes: Not reported
        Advertised link modes:  10000baseT/Full
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
        Speed: 10000Mb/s
        Duplex: Full
        Auto-negotiation: off
        Port: Direct Attach Copper
        PHYAD: 0
        Transceiver: internal
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```

enp3s0 and enp0s31f6 are 1G NIC, bridged.
```
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether a0:a3:f0:15:11:8c brd ff:ff:ff:ff:ff:ff
3: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 80:61:5f:0d:e2:c5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.101/24 brd 192.168.10.255 scope global dynamic enp1s0
       valid_lft 42692sec preferred_lft 42692sec
    inet6 2a05:6e02:1023:2410:8261:5fff:fe0d:e2c5/64 scope global dynamic mngtmpaddr 
       valid_lft 86344sec preferred_lft 86344sec
    inet6 fe80::8261:5fff:fe0d:e2c5/64 scope link 
       valid_lft forever preferred_lft forever
4: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether 8c:ec:4b:56:3e:e3 brd ff:ff:ff:ff:ff:ff
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether e6:8d:63:be:8f:e2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.10/24 brd 192.168.0.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::e48d:63ff:febe:8fe2/64 scope link 
       valid_lft forever preferred_lft forever
```
```
$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: 82599 10 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 01
       serial: 80:61:5f:0d:e2:c5
       size: 10Gbit/s
       capacity: 10Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress vpd bus_master cap_list rom ethernet physical fibre 10000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=ixgbe driverversion=5.15.0-48-generic duplex=full firmware=0x80000707, 1.2074.0 ip=192.168.10.101 latency=0 link=yes multicast=yes speed=10Gbit/s
       resources: irq:16 memory:e0000000-e007ffff ioport:e000(size=32) memory:e0080000-e0083fff memory:ef100000-ef17ffff memory:e0084000-e0183fff memory:e0184000-e0283fff
  *-network
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: a0:a3:f0:15:11:8c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-48-generic duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 ioport:d000(size=256) memory:ef020000-ef0200ff memory:ef000000-ef01ffff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (5) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 00
       serial: 8c:ec:4b:56:3e:e3
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.15.0-48-generic duplex=full firmware=0.1-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:125 memory:ef200000-ef21ffff
```
```
$ lspci -k -nn | grep -A 3 -i net
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (5) I219-LM [8086:15e3]
        Subsystem: Dell Ethernet Connection (5) I219-LM [1028:07a1]
        Kernel driver in use: e1000e
        Kernel modules: e1000e
01:00.0 Ethernet controller [0200]: Intel Corporation 82599 10 Gigabit Network Connection [8086:1557] (rev 01)
        Subsystem: Beijing Sinead Technology Co., Ltd. 82599 10 Gigabit Network Connection [1dcf:0317]
        Kernel driver in use: ixgbe
        Kernel modules: ixgbe
02:00.0 PCI bridge [0604]: Texas Instruments XIO2001 PCI Express-to-PCI Bridge [104c:8240]
03:00.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
        Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
        Kernel driver in use: r8169
        Kernel modules: r8169
```

I haven't been able to find anything relevant on the Internet so far, any help would be greatly appreciated.
Thanks

---

### Post by brazzmonkey on 2022-10-18
After several weeks trying to find out what could be the cause of such a weird behaviour, today I noticed upload and download rates are all back to normal.
But I did nothing for that, except regular system updates.
So I don't know what happened in the first place.
Anyways, this is solved.

---

