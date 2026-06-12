---
title: "need help with ethernet drivers"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by omkar_022 on 2011-01-07
i need ethernet drivers for my lan card,as u can see i already have wireless drivers for my Wi-Fi.Thanks in advance .here is the result for "lspci" command


02:00.0 Ethernet controller: Attansic Technology Corp. Device 2060 (rev c1)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at 95600000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at 3000 [size=128]
        Capabilities: <access denied>

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Askey Computer Corp. Device 7159
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 94500000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

by the way i own a Toshiba laptop satellite Pro C650....

---

### Post by stoogiebuncho on 2011-01-07
Most ethernet cards "just work" in Ubuntu.  Have you tested yours to confirm that it's not working?

If it's not working, the first thing I'd try (and maybe you've already done this) is to connect to the internet via your wireless connection and then go to System > Administration > Hardware Drivers (or something like that) and see if there are any proprietary drivers there that you can enable.

If that fails, you can try downloading the Windows drivers from the manufacturer's website, and using ndiswrapper to install them.  But I don't think I've ever heard of someone needing to do that for an ethernet card.

---

