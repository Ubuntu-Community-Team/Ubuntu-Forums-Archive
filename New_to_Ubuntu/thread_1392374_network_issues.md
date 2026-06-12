---
title: "network issues"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by tweener on 2010-01-28
greetings all.... i have been having a tough time trying to figure out my wireless network card. i recently installed ubuntu on my laptop, HP DV-7 1135nr.  anyways i came across the following command (ubuntu book)

                                 ***sudo lshw - c network***


and i got the following out put:

[B]  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:d1100000-d110ffff
  
*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:ad:2c:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)[/B]

anyways.... i was hoping someone can explain to me what **UNCLAIMED** means and how to rectify this issue.  thanks in advance for any help!!

---

### Post by tweener on 2010-01-28
oh i forgot... i did install the madwifi drivers, or at least i think i did :)

---

### Post by xifer on 2010-01-28
a node is marked as *UNCLAIMED* if no specific support for it has been loaded (or lshw has been unable to identify the driver)

from the webpage [http://lshw.org/](http://lshw.org/)

---

