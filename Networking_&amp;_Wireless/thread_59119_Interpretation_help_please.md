---
title: "Interpretation help please"
date: 2005-08-22
forum: Networking &amp; Wireless
---

### Post by tlappy on 2005-08-22
Hi all, still trying to get my modem to work. Actually having fun learning about
Linux. Anyway, I did a lspci -vvx, here are the results for my modem (I guess) But, I really don't know exactly what they mean. If a "guru" with a few extra moments could illuminate me, I would appreciate it! Thanx.....

0000:00:0d.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
        Subsystem: C-Media Electronics Inc CM8738
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 0: I/O ports at dc80 [size=64]
        Capabilities: <available only to root>
00: f6 13 11 02 01 00 10 02 20 00 80 07 00 00 00 00
10: 81 dc 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 f6 13 11 02
30: 00 00 00 00 40 00 00 00 00 00 00 00 09 02 00 00

---

### Post by MrCheese on 2005-08-23
[QUOTE=tlappy]Hi all, still trying to get my modem to work. Actually having fun learning about
Linux. Anyway, I did a lspci -vvx, here are the results for my modem (I guess) But, I really don't know exactly what they mean. If a "guru" with a few extra moments could illuminate me, I would appreciate it! Thanx.....

0000:00:0d.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
        Subsystem: C-Media Electronics Inc CM8738
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 0: I/O ports at dc80 [size=64]
        Capabilities: <available only to root>
00: f6 13 11 02 01 00 10 02 20 00 80 07 00 00 00 00
10: 81 dc 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 f6 13 11 02
30: 00 00 00 00 40 00 00 00 00 00 00 00 09 02 00 00[/QUOTE]


The CM8738 is a sound chip - also handles midi so probably looks like a comms controller at a very low level. Anyhow, the list of capabilities show what the chip can do ie. provides I/O control but not busmaster or vga snoop (to  name but two of the flags). the hex dump is simply this listing as raw data without the system interpreting it into (tech-)English.

---

