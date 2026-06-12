---
title: "Getting Online, neither wireless or wired"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by linux_agony on 2009-03-11
I've got an older laptop that I installed xubunu on. It has a broadcom 802.11b pcmcia card on it. But in order to get that working, don't I first need to get online through my wired network adaptor? Problem is I'm getting nothing there either. I even bypassed my router and hooked my laptop straight to the cable modem and still couldn't get online. It does that swirly thing, then says "disconnected". Out of curiosity I wired my dad's compaq presario to the cable modem and booted his up on the live cd. The same thing happened with his. I thought this xubuntu was supposed to be ready to use right from the start. Ubuntu says they use their OS in Africa, that must be one smart tribe. I wish I could get my laptop online because I love the clean gui interface of xubuntu. Could somebody help me please? Thanks.
Matt

---

### Post by abn91c on 2009-03-11
open a terminal and type ```
sudo dhclient eth0
```

---

### Post by linux_agony on 2009-03-11
> **abn91c said:**
> open a terminal and type ```
sudo dhclient eth0
```

I didn't get online but I'll give you the output (i typed it all)

wmaster o: unknown hardware address type 801
wmaster o: unknown hardware address type 801
listening on lpf/eth0/00:c0:9f:f7:06:4d
sending on lpf/eth0/00:c0:9f:f7:06:4d
sending on socket/fallback
dhcp discover on eth0 to 255.255.255.255 port 67 inverval 8
dhcp discover on eth0 to 255.255.255.255 port 67 inverval 7
dhcp discover on eth0 to 255.255.255.255 port 67 inverval 9
dhcp discover on eth0 to 255.255.255.255 port 67 inverval 11
dhcp discover on eth0 to 255.255.255.255 port 67 inverval 21
dhcp discover on eth0 to 255.255.255.255 port 67 inverval 5
no dhcp offers recieved
no working leases in persistent database-sleeping

---

### Post by LowSky on 2009-03-11
> **linux_agony said:**
> I've got an older laptop that I installed xubunu on. It has a broadcom 802.11b pcmcia card on it. 

Maybe we can get you the driver you need and you can install it from a flash drive.. please have the card installed and open a terminal window (menu, system, terminal) type
```
lspci -v
``` please copy and paste all the information here please.

> **linux_agony said:**
> Ubuntu says they use their OS in Africa, that must be one smart tribe. 
Matt

You really need to read up more on this distro....

Ubuntu is created and designed by Canonical, a Company operating out of England, the company was Founded by Mark Shuttleworth, who is from South Africa, the Name Ubuntu is an African word that has many meanings but basically means "the essence of being human" at least in the eyes of Archbishop Desmond Tutu

---

### Post by linux_agony on 2009-03-11
> **LowSky said:**
> Maybe we can get you the driver you need and you can install it from a flash drive.. please have the card installed and open a terminal window (menu, system, terminal) type
```
lspci -v
``` please copy and paste all the information here please.


OK, from now on I'll be on my own laptop. Which by the way doesn't give me the wireless option at the top right and no swirlee icon. Maybe that's because I don't even see it listed here, do you?

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
	Kernel modules: intel-rng, iTCO_wdt

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

---

