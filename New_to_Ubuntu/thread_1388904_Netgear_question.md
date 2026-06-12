---
title: "Netgear question"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-01-23
my friend has a netgear card that plugs into a pci slot on the mobo. its not recgonizing the card hes using Karmic

---

### Post by cariboo on 2010-01-23
Have you tried it in another computer, or a computer running windows? 

What is the output of:

```
lspci
```

and

```
sudo lshw -C network
```

---

### Post by Extract_Here on 2010-01-23
heres what it said 


nathan@nathan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
nathan@nathan-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: 00:30:1b:b1:c6:e8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:9000(size=256) memory:f5020000-f50200ff memory:40000000-4000ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:f5000000-f500ffff memory:f5010000-f501ffff
nathan@nathan-desktop:~$

---

