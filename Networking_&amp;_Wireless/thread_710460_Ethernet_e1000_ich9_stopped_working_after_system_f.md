---
title: "Ethernet e1000_ich9 stopped working after system freeze"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by ngu on 2008-02-28
kubuntu 2.6.22-14-generic , installed ~ 2 months ago. 

Prehistory: 
When I, as usually, plug my iPod into the USB port, the system unexpectedly freezes, I can do nothing in the KDE nor can I switch to the terminal (Alt-F1). I do the reboot by pressing the 'harsh reboot' button on the system case. System boots ok except for the ethernet interface. No modules are loaded, no /dev/eth0 whatsoever.

**modprobe e1000-ich9** doesn't make device to appear.  

After examining outputs of various commands and comparing them with ones on the same box next desk, I see some differences. His *lspci --nn* shows 
```
00:03.0 Communication controller [0780]: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller [8086:29c4] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82801I (ICH9 Family) Gigabit Ethernet Controller [8086:294c] (rev 02)
```
while mine does:
```
00:03.0 Communication controller [0780]: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller [8086:29c4] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation **[COLOR="Red"]Unknown device[/COLOR]** [8086:**[COLOR="Red"]0000[/COLOR]**] (rev 02)
```
working lspci --v: 
```
00:19.0 Ethernet controller: Intel Corporation 82801I (ICH9 Family) Gigabit Ethernet Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 0001
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at 90380000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at 903a4000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 20e0 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [e0] Vendor Specific Information

```
whereas on my workstation: 

```
00:19.0 Ethernet controller: Intel Corporation **[COLOR="Red"]Unknown device 0000[/COLOR]** (rev 02)
        Subsystem: Intel Corporation Unknown device **[COLOR="Red"]0000[/COLOR]**
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to **[COLOR="Red"]IRQ 9[/COLOR]**
        Region 0: Memory at 90380000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at 903a4000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 20e0 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [e0] Vendor Specific Information

```

These zeros do seem very suspicious to me, but I don't have any clue what to do next. 
Questions:
[LIST]
[*]Can it be an unrecoverable h/w failure? Is there an easy way to prove it to the IT guys (who are in the realm of MS) w/o installing windows :) ?
[*]Could this be an issue similar to described here: [http://www.matinfo.ch/blog/archive/2007/01/26/intel-nic-pxe-e05-error.html](http://www.matinfo.ch/blog/archive/2007/01/26/intel-nic-pxe-e05-error.html) , where EEPROM of my unfortunate network adapter was polluted by some usb/iPod/whatever glitch? 
[/LIST]

Thank you!

---

