---
title: "[SOLVED] RTL8180L 802.11b Wireless not working"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by pirabu on 2008-05-20
RTL8180L 802.11b Wireless not working.

Under System>networks my wireless connection is not showing at all. 

Here is the  lspci -v output. Any help would be appreciated. 

```
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at 8800 [size=256]
	Memory at e9000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Sony Corporation Unknown device 80ea
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 8400 [size=256]
	Memory at e8800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

---

### Post by pirabu on 2008-05-21
Installed the Windows Driver following the Wifi Docs suggestion. It works fine now.

---

