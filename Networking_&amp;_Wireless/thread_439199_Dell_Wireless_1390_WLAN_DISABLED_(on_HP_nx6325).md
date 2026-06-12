---
title: "Dell Wireless 1390 WLAN DISABLED (on HP nx6325)"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by user5566 on 2007-05-10
Hello,

Can anyone tell me how to enable my Wireless card, please?

I use Ubuntu on my HP Compaq nx6325 (EY577ES#AKN) notebook.

This is lshw listing:
> 

        *-pci:3
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: Dell Wireless 1390 WLAN Mini-PCI Card
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@30:00.0
                logical name: eth1
                version: 01
                serial: 00:14:a5:d9:34:ec
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:c8000000-c8003fff irq:18



---

