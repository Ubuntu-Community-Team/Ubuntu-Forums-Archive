---
title: "rtl8139b on Ubuntu Server - unrecognized"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by alanfranz on 2006-09-18
Hello, I'm experiencing a problem with a Realtek RTL8139B PCI Card mounted on an IBM Netfinity 5100 on Ubuntu Server. The card is not recognized, no driver gets loaded for it.

lspci output:
```
0000:00:09.0 Ethernet controller: Unknown device 0001:8139 (rev 10)
 Subsystem: Realtek Semiconductor Co., Ltd.: Unknown device 8139
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
 Latency: 48 (8000ns min, 16000ns max)
 Interrupt: pin A routed to IRQ 209
 Region 0: I/O ports at 2200 [size=256]
 Region 1: Memory at feb7f800 (32-bit, non-prefetchable) [size=256]
 Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

i tried modprobing 8139cp, 8139too and via-rhine with no success.

Any idea?

---

