---
title: "Wireless Card not even recognized in xubuntu"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by linux_agony on 2009-03-15
Hi you all. At least I finally got my xubuntu 8.1 system online. The wireless didn't work, and I couldn't get online through my ethernet card, neither straight to the cable modem or the router. But I did get online through the Targus docking station that has ethernet to USB. The Targus is connected to the router. I wonder why that is? Maybe it's because when I ran the router setup disk in windows, I was using the Targus? And I remember the setup saying it was configuring the router AND modem. Also since I had MAC address filtering in my router, I had to add that one in xubuntu under edit-connections-wired. What is that address too? It's not a card, I'm using USB. 

Well whatever I'm online now. Internet seems a tad sluggish but that may be because I'm connecting through USB 1.0. Now back to my original task, getting the wireless card working. I've typed in LSPCI -v but I don't see anything. Can you check this?

matt@matt-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, fast devsel, latency 0
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: e8100000-e81fffff
	Prefetchable memory behind bridge: f0000000-f7ffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: e8200000-e82fffff
	Prefetchable memory behind bridge: 20000000-23ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 24000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: medium devsel, IRQ 11
	I/O ports at 1100 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: medium devsel, IRQ 11
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e8120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e8204000 (32-bit, non-prefetchable) [size=2K]
	Memory at e8200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 64, IRQ 9
	I/O ports at 4000 [size=256]
	Memory at e8204800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

02:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: CLEVO/KAPOK Computer Device 5600
	Flags: bus master, medium devsel, latency 168, IRQ 5
	Memory at e8205000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 28000000-2bfff000
	I/O window 0: 00004400-000044ff
	I/O window 1: 00004800-000048ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

The card is an Inventel WL-611BC. The bright power light isn't even lit on it, it does work in windows though. In Synaptic Package Manager I installed B43-FWCUTTER. During install I checked "extract firmware". Obviously It didn't do anything. I didn't really want to invest in any cards for this machine, It's just an old crumby, hold me over laptop.

---

### Post by diablo75 on 2009-03-15
You might try using Windows based drivers to get your wireless working.  Check this link out:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

That will tell you how to install ndiswrapper, and how to use it to install Windows based drivers.

---

