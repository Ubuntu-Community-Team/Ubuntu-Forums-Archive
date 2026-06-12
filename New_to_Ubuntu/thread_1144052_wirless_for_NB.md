---
title: "wirless for NB"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by mymaydayya on 2009-04-30
I am trying to use wifi on ubuntu 8.10, but I don't know well about it.
Can someone help me?


I tried reading some guides, I think I should first get the driver.
after 
lspci -v | less
I got some message, but still can't figure out which driver I should get.

help please

04:00.0 Network controller: RaLink Device 0781
	Subsystem: Foxconn International, Inc. Device e002
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d6700000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0140
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	I/O ports at 2000 [size=256]
	Memory at d2410000 (64-bit, prefetchable) [size=4K]
	Memory at d2400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d2420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by cmnorton on 2009-04-30
Is Network Manager running? This would be an icon that is probably on the upper right hand-side of your desktop.

What are the contents of /etc/network/interfaces

cat /etc/network/interfaces

---

### Post by cmnorton on 2009-05-01
Here are some things to try.

1) Uninstall and re-install Network Manager.

2) Try adding Network Manager to one of your toolbars by right clicking on the toolbar and following the Add Application links.

---

