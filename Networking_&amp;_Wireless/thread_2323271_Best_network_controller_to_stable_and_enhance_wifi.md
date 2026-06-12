---
title: "Best network controller to stable and enhance wifi connection."
date: 2016-05-04
forum: Networking &amp; Wireless
---

### Post by jorge39 on 2016-05-04
Hello!

I recently installed ubuntu 14.04 LTS and I dual-boot windows 10 with ubuntu 14.04 LTS. In windows my wireless connect is much stronger and it isn't as stable as in windows 10.

So I was wondering which network controller should I intall.

I did ```
lspci -v
``` and the result is:

```
08:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)    Subsystem: Hewlett-Packard Company Device 2154
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at b7600000 (64-bit, non-prefetchable) [size=32K]
    Memory at b7400000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: wl


0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 1967
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at b4000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci


10:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Device 1967
    Flags: bus master, fast devsel, latency 0, IRQ 29
    I/O ports at 3000 [size=256]
    Memory at b7800000 (64-bit, non-prefetchable) [size=4K]
    Memory at b7700000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

```

What controllers should I install? :)

Thanks!

---

