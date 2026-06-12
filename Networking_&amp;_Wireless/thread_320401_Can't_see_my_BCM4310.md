---
title: "Can't see my BCM4310"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by unreal on 2006-12-17
I have a Compaq Presario notebook with a Broadcom 4310 wireless adapter. I have tried both the ndiswrapper and the FWcutter methods of getting it to work, but for some reason my network manager doesn't even see my card.

Command: lspci -vvv gets:

03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1360
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 255
        Region 0: Memory at b3200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Command ndiswrapper -l gets me:

Installed drivers:
bcmwl5          driver installed, hardware present 
bcmwl5a         driver installed 
oem3            driver installed 

I have tried installing and rebooting and am still having no luck even seeing my card in the network manager. Am I missing something? Please help.

---

### Post by Doug11 on 2006-12-17
Are you getting the light to come on for our wireless card?

---

### Post by unreal on 2006-12-17
well that's the thing. the light comes on but I think that has something to do with the fact that my wireless and bluetooth are on the same switch. And my bluetooth works just fine.

---

### Post by unreal on 2006-12-17
Strangest thing. All of a sudden it works. I have no idea what I did.

---

### Post by ineluki12 on 2007-01-08
Unreal,
How's that 4310 working for you? I'm using the latest ndiswrapper and dell driver, but the card will quit on me after about 5 or 10 mins. If I have a terminal up, it'll say something like 'disabling IRQ 7'. Have you encountered this problem?

---

### Post by vigyani on 2007-02-06
I used the fwcutter method given on the link: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

To use network manager, network devices should not be configured manually. If any network device is configured manually it is ignored by the network-manage.

I hope this helps.

---

