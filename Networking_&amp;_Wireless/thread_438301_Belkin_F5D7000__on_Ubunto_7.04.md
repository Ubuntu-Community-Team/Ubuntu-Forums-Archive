---
title: "Belkin F5D7000  on Ubunto 7.04"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by andytx on 2007-05-09
Hi all, 
I haveBelkin F5D7000 PCI, ubuntu does not recognize and on Admin network does not see Wireless.
Woul you guys help me how to install step by step, and also Logictech Orbit Mp Webcam usb I'm new to linux.

Thank you

---

### Post by chili555 on 2007-05-09
There are three or more versions with different chipsets. Please, from a terminal,  post the result of:```
lspci -vv | grep Network
```Let's see if we can narrow it down.

---

### Post by andytx on 2007-05-09
with this command  lspci -vv | grep Network 
It's does nothing
if with this command alone lspci -vv 
it's show  below
05:06.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
        Subsystem: Belkin Unknown device 700f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at ba00 [size=256]
        Region 1: Memory at fd9ff000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

Thanks

---

### Post by chili555 on 2007-05-09
Let's see ```
sudo lshw -C network
```Thanks.

---

