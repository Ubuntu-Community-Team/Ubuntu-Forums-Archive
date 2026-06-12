---
title: "NIC duplex"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by tweener on 2010-03-16
hi all.... i was not getting the transfer rates on my new install so i did an lshw and found my network card was only set at half duplex.... i wanna change it to full duplex & change the capacity, how do i do it?

thanx.

                                  [FONT=Georgia, serif]***-network**[/FONT]
 [FONT=Georgia, serif]description: Ethernet interface[/FONT]
 [FONT=Georgia, serif]product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT]
 [FONT=Georgia, serif]vendor: Realtek Semiconductor Co., Ltd.[/FONT]
 [FONT=Georgia, serif]physical id: 0[/FONT]
 [FONT=Georgia, serif]bus info: pci@0000:0a:00.0[/FONT]
 [FONT=Georgia, serif]logical name: eth0[/FONT]
 [FONT=Georgia, serif]version: 02[/FONT]
 [FONT=Georgia, serif]serial: 00:1e:ec:ad:2c:f3[/FONT]
 [FONT=Georgia, serif]size: 10MB/s[/FONT]
 [FONT=Georgia, serif]capacity: 100MB/s[/FONT]
 [FONT=Georgia, serif]width: 64 bits[/FONT]
 [FONT=Georgia, serif]clock: 33MHz[/FONT]
 [FONT=Georgia, serif]capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT]
 [FONT=Georgia, serif]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ***duplex=half*** latency=0 link=no multicast=yes port=MII speed=10MB/s[/FONT]
 [FONT=Georgia, serif]resources: irq:29 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)[/FONT]

---

### Post by VoodooLoveDog on 2010-03-16
If it's set to autonegotiate and you are getting half-duplex then you may need to take a look at both sides of the physical connection. Can the switch/router/bridge/etc. you are plugging into negotiate a full-duplex connection?

You can try to force your interface to full-duplex, but this may sever your connection.

---

### Post by tweener on 2010-03-16
when i had w7 rc running, i had set all my computers to full duplex with no problems and the transfer rate was around 10 or 11 MB/sec...... now however, i only get about 7 or 8 MB/sec. so if i wanna change it can i and if so how? i am guessing i have to edit a config file but which one and where is it located...... any help would be much appreciated.

---

### Post by tweener on 2010-03-16
anyone with a suggestion please...... :cry:

---

