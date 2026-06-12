---
title: "Network widget sometimes doesn't list interfaces or wifi networks"
date: 2015-05-21
forum: Networking &amp; Wireless
---

### Post by The Cog on 2015-05-21
Sometimes, maybe one in 4 times I boot, and maybe once a day while I'm browsing, my network widget decides not to list any interfaces or nearby wifi networks. See attached screenshot.

Sometimes running sudo iwlist scan makes the wifi list reappear, sometimes disabling and re-enabling wifi or networking fixes it. This has only happened since I upgraded (clean install) to version 15.04 (14.04 and 14.10 didn't do this).

Has anyone else seen this? Anyone know a fix?

lspci -v shows these networking components:
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 188b
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at 2000 [size=256]
	Memory at f0004000 (64-bit, prefetchable) [size=4K]
	Memory at f0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 08-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169

07:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-00-79-34-b5-30-35-54
	Kernel driver in use: rt2800pci

```

---

