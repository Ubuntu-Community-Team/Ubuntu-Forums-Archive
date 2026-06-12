---
title: "BCM max strength at 55%"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by so-crates on 2007-08-10
Hello everyone,

as you can tell by how many "cups of ubuntu" I've had, I'm rather new to ubuntu. I'm not new to linux however and can try suggestions that might be a bit more advanced. Any help or comment at all is really appreciated..

So I have a broadcom wireless card. They are pains, right.. I figured out how to get this thing to work with ndiswrapper before in debian about 2 years ago, and was going to do the same thing this time when I noticed dmesg said "can't load module bcm**** blah blah blah *.fw -- that's when I realized.. hey this ubuntu is so good it's trying to load my broadcom! great, so I decided to work with that. I found through doing some googlizing around that someone downloaded the firmware file through this bcm**fwcutter app, so I apt-get installed it and great, it worked. Now the issue is that even though I am literally a few feet from my wireless router, my status monitor in gnome says that I am connected at 55%. I am wondering why there is this bottleneck and if there is a known way of adjusting it. Here is some detailed information for anyone interested in taking a look:

OS : Fiesty Fawn 
Architecture: Amd64 bit
Computer: Laptop, PresarioV2000 (Compaq)
Hardware: lspci -vv gives this about my component:

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1355
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at d0204000 (32-bit, non-prefetchable) [size=8K]

Hope that's enough info, any help again is greatly appreciated!

Cheers

---

### Post by ddrichardson on 2007-08-10
Not familiar with your hardware, but low signal strength is often a result of interference from other appliances. Try changing to another channel on your router/card.

---

### Post by bmartin on 2007-08-11
I have the same card as you. Don't use fwcutter (i.e. the firmware). Use ndiswrapper instead. The BCM4318 chipset has known "power issues" with the BCM43xx kernel module, plus your maximum connection speed is 11mbps.

[This thread]("http://ubuntuforums.org/showthread.php?t=405990") should be of help to you. I don't know if it'll resolve your limited connection strength, but it's worth a shot. It's an automatic installer; there's no command prompt involved. If ndiswrapper doesn't work out, it allows you to go back to the firmware.

---

