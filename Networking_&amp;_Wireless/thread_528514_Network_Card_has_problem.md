---
title: "Network Card has problem"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by moonoi on 2007-08-18
> Aug 16 13:27:44 ubuntu kernel: [43469510.420000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:29:49 ubuntu kernel: [43469635.420000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:31:49 ubuntu kernel: [43469755.430000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:33:54 ubuntu kernel: [43469880.430000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:35:59 ubuntu kernel: [43470005.430000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:38:19 ubuntu kernel: [43470145.430000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:41:04 ubuntu kernel: [43470310.430000] NETDEV WATCHDOG: eth1: transmit timed out
Aug 16 13:46:34 ubuntu kernel: [43470640.430000] NETDEV WATCHDOG: eth1: transmit timed out

> 
             *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 3
                bus info: pci@05:03.0
                logical name: eth1
                version: 14
                serial: 00:14:78:03:43:96
                size: 1GB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=off broadcast=yes driver=skge driverversion=1.5 duplex=full firmware=N/A ip=61.47.61.78 link=yes multicast=yes port=twisted pair speed=1GB/s
                resources: iomemory:dfcfc000-dfcfffff ioport:ac00-acff irq:50

My gigabit network card has some problem on Ubuntu box. It was stopping while this errors occured.
This problem never occurs while I using 100Mbps Onboard Network Card.

(Sorry, my English is bad)

Thank You :)

---

