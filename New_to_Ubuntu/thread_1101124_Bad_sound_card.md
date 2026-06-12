---
title: "Bad sound card"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Pbethe on 2009-03-20
I have this old computer that I want to keep in service.  It exceeds the minimums for running Ubuntu except for one thing.  It has a motherboard with a built-in sound card, and the sound stopped working years ago.  I think the sound is dead.  Ubuntu.com says that you should have a sound card to run its distro.  Assuming that the hardware has gone bad, how worried should I be about the lack of a working sound card?

---

### Post by InfectedWithDrew on 2009-03-20
Without sound, you won't be able to enjoy the delicious sounds of music!

But otherwise, you won't have any problems.  You don't need to hear the sound that Ubuntu makes as it boots or anything like that.

----------------
Now playing: [Emery - Say The Things (You Want)](http://www.foxytunes.com/artist/emery/track/say+the+things)

---

### Post by coolbrook on 2009-03-20
Do you have free PCI slots?  Consider eBay or craigslist for an old entry-level sound card. At 5-10 bucks, you can't go wrong.

---

### Post by Pbethe on 2009-03-20
> **coolbrook said:**
> Do you have free PCI slots?  Consider eBay or craigslist for an old entry-level sound card. At 5-10 bucks, you can't go wrong.

I have the case open now, but I don't know how to ID a PCI slot.  I did learn this in a forum somewhere:   sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
	Flags: bus master, medium devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 1.0
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: d4000000-d7ffffff
	Prefetchable memory behind bridge: 20000000-200fffff
	Capabilities: [80] Power Management version 2
	Kernel modules: shpchp

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
	Subsystem: VIA Technologies, Inc. Device 0000
	Flags: bus master, stepping, medium devsel, latency 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e000 [size=16]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
	Subsystem: First International Computer, Inc. Device 1234
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at e400 [size=32]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
	Flags: medium devsel
	Kernel modules: i2c-viapro

00:11.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
	Subsystem: Netgear Device f311
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at e800 [size=256]
	Memory at d9000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 20100000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: natsemi
	Kernel modules: natsemi

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
	Subsystem: ATI Technologies Inc Device 0084
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 11
	Memory at d4000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at d000 [size=256]
	Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: [50] AGP version 1.0
	Kernel modules: atyfb
Anyway, I do have a newer laptop where I can play my favorite videos with sound.  For playing music, I even have a Walkman and a stereo system with a **turntable!**

Paul   :D

---

### Post by coolbrook on 2009-03-20
Here's what they look like

[http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect](http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect)

---

### Post by markbuntu on 2009-03-20
You could always get a usb sound thingy.

---

