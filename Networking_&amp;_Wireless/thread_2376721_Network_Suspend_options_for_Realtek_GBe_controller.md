---
title: "Network Suspend options for Realtek GBe controller?"
date: 2017-11-05
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2017-11-05
I'm running Kubuntu 16.10 on an AMD FX-8350 box. My AsRock mobo has an onboard RealTek GbE controller, like so:

$lspci -v 
.
. 
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
        Subsystem: ASRock Incorporation Motherboard (one of many)
        Flags: bus master, fast devsel, latency 0, IRQ 36
        I/O ports at c000 [size=256]
        Memory at d2104000 (64-bit, prefetchable) [size=4K]
        Memory at d2100000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

When my system suspends, it deactivates the ethernet adapter, and when I subsequently wake the system I have to wait for the system to reactivate the adapter. Is there a way to leave the ethernet adapter activated during suspend?

Thx, Gus

---

