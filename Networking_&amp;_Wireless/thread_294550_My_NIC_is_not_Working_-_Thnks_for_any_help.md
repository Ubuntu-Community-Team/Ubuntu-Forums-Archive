---
title: "My NIC is not Working - Thnks for any help"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by shansonfw on 2006-11-06
Noob - :confused: 

New 6.10 Edgy install.

I have no ethernet connectivity. I plug an ethernet cable into my NIC and router and nothing happens.

I have gone into the System > Administration > Networking and the NIC is listed. I open properties and check "Enable". But, nothing...

I get the following when I run lshw:


*-network:1 DISABLED
description: Ethernet interface
product: 82801DB PRO/100 VM (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@05:08.0
logical name: eth0
version: 81
serial: 00:0b:cd:1e:8b:89
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 multicast=yes
resources: iomemory:fca00000-fca00fff ioport:1000-103f irq:209


When I first saw "*-network:1 DISABLED" I went back and checked the Networking GUI and it still had the Enable check box checked.

Any help would be appreciated.

---

