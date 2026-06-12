---
title: "Drivers for Linux 2.4.x are good for Linux 2.6.28-11-generic?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by doctorphoto on 2009-05-06
Hallo I'm back with more information, my computer is a potpoury(?) with Athlon AMD processor and uses a wired ethernet connection (Realtek RTL 8169/8110 family gigabit ETHERNET NIC) to internet.
I think that i know the problem now, I think that ubuntu does not recognize the ethernet and so I tried to install the driver but as a "very very absolut beginner" its quite hard for me to find out if the driver for linux 2.4.x is suitable even for the ubuntu version (Kernel linux 2.6.28-11-generic).
And even the makefile file is still hard to understand for me can any one help me how to use?
Thanks a lot Marcus

---

### Post by tomcheng76 on 2009-05-06
post your output of "lspci -vv"
is there anything like this
> 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Giga-byte Technology Device e000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 2298
        Region 0: I/O ports at c000 [size=256]
        Region 2: Memory at fa000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at fd100000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

---

