---
title: "Netgear WG311v3 support"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by wbiggers on 2005-12-01
I've been running wireless on one of my linux machines for a couple of months using a Netgear WG311T.  It worked great out of the box and I guess I got over-confident.  I needed to install wireless on another linux box so I went and purchased another Netgear card.  However, the 'T' version was more expensive so I bought the plain vanilla WG311.  When I put it in the computer, it isn't recognized.

I did some checking from the WIKI site and found that the WG311v2 is supported out of the box but there is no mention of the v3.  I checked the card I installed and ... yep - it's the v3.

So I thought I'd start a thread and see if anyone could help me get the v3 card working.  I couldn't find any new drivers on the Netgear web site but I'll admit I didn't have a lot of time to search there.

---

### Post by Lambert on 2005-12-01
If you run the command

lspci -v

and

lspci -n

post the output.

---

### Post by wbiggers on 2005-12-01
Thanks for the quick response.  I'll have to wait until I get home tonight to run the commands and post the output.  I should have mentioned in my original post that I am running Breezy 5.10.

---

### Post by wbiggers on 2005-12-02
OK - I ran the two commands you requested above.

Here is the output from lspci -v:

--------------------------

0000:00:00.0 Host bridge: Intel Corp. 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
	Flags: bus master, fast devsel, latency 0

0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
	Subsystem: Intel Corp.: Unknown device 7123
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [dc] Power Management version 1

0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f4100000-f41fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02) (prog-if 80 [Master])
	Subsystem: Intel Corp. 82801AA IDE
	Flags: bus master, medium devsel, latency 0
	I/O ports at 10a0 [size=16]

0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corp. 82801AA USB
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1080 [size=32]

0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
	Subsystem: Intel Corp. 82801AA SMBus
	Flags: medium devsel, IRQ 9
	I/O ports at 10b0 [size=16]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
	Subsystem: Intel Corp.: Unknown device 5643
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1200 [size=256]
	I/O ports at 1300 [size=64]

0000:01:08.0 Communication controller: Lucent Microelectronics LT WinModem
	Subsystem: Risq Modular Systems, Inc.: Unknown device 044e
	Flags: fast Back2Back, medium devsel, IRQ 9
	Memory at f4120000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 2800 [size=8]
	I/O ports at 2000 [size=256]
	Capabilities: [f8] Power Management version 2

0000:01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139
	Flags: bus master, medium devsel, latency 64, IRQ 9
	I/O ports at 2400 [size=256]
	Memory at f4120400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

0000:01:0a.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
	Subsystem: Netgear: Unknown device 6b00
	Flags: 66MHz, medium devsel, IRQ 10
	Memory at f4110000 (32-bit, non-prefetchable) [size=64K]
	Memory at f4100000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2

----------------------------

Here is the output of lspci -n

----------------------------

0000:00:00.0 0600: 8086:7124 (rev 03)
0000:00:01.0 0300: 8086:7125 (rev 03)
0000:00:1e.0 0604: 8086:2418 (rev 02)
0000:00:1f.0 0601: 8086:2410 (rev 02)
0000:00:1f.1 0101: 8086:2411 (rev 02)
0000:00:1f.2 0c03: 8086:2412 (rev 02)
0000:00:1f.3 0c05: 8086:2413 (rev 02)
0000:00:1f.5 0401: 8086:2415 (rev 02)
0000:01:08.0 0780: 11c1:044e
0000:01:09.0 0200: 10ec:8139 (rev 10)
0000:01:0a.0 0200: 11ab:1faa (rev 03)

-------------------------

If I read the output file for lspci -v correctly, the device in question is the last one listed.

Thanks,
Wes

---

### Post by Lambert on 2005-12-02
You'll need to use an app called ndiswrapper. It basically makes the windows drivers work in linux.

There's a link in my signature for ndiswrapper.

I didn't see a driver link on the ndiswrapper site so you can try to get this working with the drivers from your cd. Try xp drivers first, if they don't work then try win2000 drivers.

If none of those work then try drivers from another card with the same pci id as yours. Your pci id is 11ab:1faa and there's a trendware card that matches it. that might/might not work but try drivers off your cd first.

---

### Post by wbiggers on 2005-12-02
I connected my PC to the internet (wireline) and used synaptic to download ndisgtk and the dependencies.  All went well with that installation.  I copied the drivers (.inf and .sys files) from the install cd to my hard drive.  I then used NDISWRAPPER to install those drivers.  The driver would install fine and in the NDISGTK screen it would indicate "hardware found: Yes".  However, when I went to Network Configuration to set up the wireless cards, there was no wireless card indicated.  I checked lspci again and the display was the same as above.

I repeated it all with the WIN2K drivers with the same result.  From the NDIS WIKI link, I searched for the pci id number and found a couple of other web addresses with drivers for the same pci id.  The link for [www.marvell.com](www.marvell.com) seemed to me to be very promising since the lspci dump indicates the chip is from Marvell Tech.  However, that site wouldn't respond.  I also found drivers under Trendnet and those downloaded like a champ.  I really thought i was in business because the file names appear to be those from the marvell company.  However, I couldn't even get those files to install with ndisgtk.

Bottom line, I'm still leashed by a string of copper running through my living room.  I guess I'll take the wg311v3 card back tomorrow and see if they still have any v2 cards on the shelf.  I saw some a few days ago when I started this effort.  I just goes to show that the newest isn't always the best...and do you homework on compatible cards BEFORE making 3 trips to the store.

---

### Post by raghav_p on 2005-12-02
By the way, the WG311v2 is supported well out of the box. Installed one a few days ago :)

---

### Post by wbiggers on 2005-12-04
I exchanged my v3 for a v2 card.  It seems to be supported but I'm still having lots of problems.  The card won't connect to any wifi network.  It shows up fine so the driver is talking to the card, but it doesn't want to work with even simple scanning commands like iwlist wlan0 scanning - I get the message

wlan0     Failed to read scan data : Resource temporarily unavailable

By the way, when I used a WG311T card (borrowed from another PC), it worked great but showed up as "ath0".  This one shows up as "wlan0".  Is there a difference?

---

