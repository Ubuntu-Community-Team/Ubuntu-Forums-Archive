---
title: "Ubuntu 20.04 no wi-fi"
date: 2022-04-08
forum: Networking &amp; Wireless
---

### Post by gnostlos on 2022-04-08
I downloaded 20.04 and cannot connect to wi-fi. My 18.04 has always connected. Searching for the driver, I find that there is one:
lspci -vvnn | grep -A 9 Network=>
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
        Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0019]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at f7200000 (64-bit, non-prefetchable) [size=32K]
        Region 2: Memory at f7000000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: bcma, wl

The controller is essentially the same as for version 18.04, but it says "access denied". What does one do to gain access?
Item: The command "rfkill list all" lists only Bluetooth, indicating that it does not see wi-fi as a device.

---

