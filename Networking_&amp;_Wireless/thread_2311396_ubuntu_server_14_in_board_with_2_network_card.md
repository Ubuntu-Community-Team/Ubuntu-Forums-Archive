---
title: "ubuntu server 14 in board with 2 network card"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by joe194 on 2016-01-26
I installed Ubuntu server into a x86 board with 2 network cards. Problem is every time it turns on there is only one net card working. "ifconfig -a" show lo and p1p1(logical name of one net card).
"lshw -class network" shows 2 cards, but the second card does not have logical name.

[COLOR=#000000][FONT=Lucida Grande]*-network [/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]logical name: p1p1[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]version: 06[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]serial: 00:0b:ab:a8:9e:94[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]size: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.100.201 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]resources: irq:89 ioport:d000(size=256) memory:90604000-90604fff memory:90600000-90603fff[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]*-network UNCLAIMED[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]description: Ethernet controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]bus info: pci@0000:04:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]version: 06[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]capabilities: pm msi pciexpress msix vpd cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]resources: ioport:2000(size=256)[/FONT][/COLOR]

then reboot it,2 net card become working. "lshw -class network" show that:

[COLOR=#000000][FONT=Lucida Grande]*-network [/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]logical name: p1p1[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]version: 06[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]serial: 00:0b:ab:a8:9e:94[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]size: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.100.201 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]resources: irq:89 ioport:d000(size=256) memory:90604000-90604fff memory:90600000-90603fff[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]*-network UNCLAIMED[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]description: Ethernet controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]bus info: pci@0000:04:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]version: 06[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]capabilities: pm msi pciexpress msix vpd cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]resources: ioport:2000(size=256)[/FONT][/COLOR]

I checked the Ubuntu document said edit the /etc/udev/rules.d/70-persistent-net.rules , but I found there was no such file.

---

### Post by papibe on 2016-01-26
Hi joe194. Welcome to the forum ):P

I'd start by booting into the BIOS and making sure the 2nd card is enable from there.

Hope it helps. Let us know how it goes.
Regards.

---

