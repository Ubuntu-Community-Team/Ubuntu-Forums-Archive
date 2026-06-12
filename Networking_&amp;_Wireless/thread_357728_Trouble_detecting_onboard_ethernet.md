---
title: "Trouble detecting onboard ethernet"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by rljacobson on 2007-02-10
Hi. I'm having trouble getting my onboard NIC working. I have Ubuntu 6.10 running on an [Abit NF-M2S]("http://www.abit-usa.com/products/mb/products.php?categories=1&model=332") motherboard which has some kind of onboard Realtek ethernet that apparently does not work "out of the box" with Ubuntu 6.10. 

"lspci" outputs the following ethernet-related lines:

01:05.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8167 (rev 10)

The Linksys card I recognize as a NIC I am using temporarily until I get the onboard NIC working.

"lspci -vv" gives the following for the Realtek device:

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8167 (rev 10)
        Subsystem: ABIT Computer Corp. Unknown device 1c2b
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 209
        Region 0: I/O ports at c800 [size=256]
        Region 1: Memory at fd9fe000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at fd920000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

I don't know if a driver is loading for this device, or what else could be wrong. I'd appreciate any help.

--Robert

---

### Post by gradedcheese on 2007-02-10
So you're saying it doesn't show up when you run "ifconfig"?

---

### Post by rljacobson on 2007-02-10
That is correct.

---

### Post by gradedcheese on 2007-02-10
ouch :(  It's probably a very new chipset that the community hasn't had a chance to get documentation for (or reverse-engineer).  It would be useful to figure out what the chipset is.  Probably the easiest way (er, if I was doing it) is to check the motherboard's manual and, failing that, to just look at the Realtek chip on the board and find the part number.  After that a google search should reveal the state of the driver (if any) and what you need to do to get it.  It looks like the manual is:

[http://www.abit-usa.com/downloads/downloads.php?file=/downloads/manual/english/nf-m2s.zip](http://www.abit-usa.com/downloads/downloads.php?file=/downloads/manual/english/nf-m2s.zip)

I hope that helps.  If you can, post the chipset info once you find it and maybe a few other people can search around too.

---

### Post by rljacobson on 2007-02-10
I have resolved my problem. The user manual is useless. The NIC chip on the mainboard is printed with the following:
RTL8110SC
6919252
G640B

The first thing is the model # for a Realtek product supported by the r1000 driver, which Realtek distributes on its website. I downloaded the latest driver, compiled and installed it, and then was able to activate it with the Network applet.

---

### Post by gradedcheese on 2007-02-10
Excellent, good work! :)  If you have the time, write to Realtek and thank them for making the driver available and encourage them to keep doing that with their future products.

---

