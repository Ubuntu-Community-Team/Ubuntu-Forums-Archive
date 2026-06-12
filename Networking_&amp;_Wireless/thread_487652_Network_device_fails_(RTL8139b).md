---
title: "Network device fails (RTL8139b)"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by curiousben on 2007-06-29
Hello. I have recently installed Feisty Server on my x86 box, and I cannot for the life of me get my network card to work. I have a Realtek 8139, and DHCP or manual IP settings both timeout repeatedly. 

This machine has worked fine with net connectivity on Win2k, WinXP, Hoary Hedgehog, and Mandrake 10. Though it's been so long, that I don't remember if I had to do anything fancy for Hoary or Mandrake 10. I remember ACPI was not working properly on those distros (more on this later).

I have a router which is working fine with other machines on the network, with the DHCP server intact and dishing out IP's normally.

I have attached the dump of lspci at the end of this post. (update: put up proper version without access denied messages)

After digging online for a bit I suspect this may be an issue with ACPI. I followed this thread:
[http://lists.debian.org/debian-kernel/2005/08/msg00102.html](http://lists.debian.org/debian-kernel/2005/08/msg00102.html) to get some clues but was unable to find a solution. 

Any help you can offer would be appreciated.

Ben




> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8083
	Flags: bus master, medium devsel, latency 32
	Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: [c0] AGP version 2.0

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e7000000-e7ffffff
	Prefetchable memory behind bridge: eff00000-febfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
	Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
	Flags: medium devsel
	I/O ports at e600 [size=32]

00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8083
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at e6800000 (32-bit, non-prefetchable) [size=4K]

00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8083
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at e6000000 (32-bit, non-prefetchable) [size=4K]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8083
	Flags: bus master, fast devsel, latency 128
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at d800 [size=16]

00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: ASUSTeK Computer Inc. CMI8738 6ch-MX
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
	I/O ports at b000 [size=256]
	Capabilities: [c0] Power Management version 2

00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: ATI Technologies Inc ATI TV Wonder Pro
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: [dc] Power Management version 1

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
	Subsystem: Creative Labs Gameport Joystick
	Flags: bus master, medium devsel, latency 32
	I/O ports at a400 [size=8]
	Capabilities: [dc] Power Management version 1

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Surecom Technology EP-320X-R
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at a000 [size=256]
	Memory at e4800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1) (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device 807b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at effe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0


---

### Post by curiousben on 2007-06-29
I edited menu.lst to add a grub entry with acpi=off, but still no luck.

I should mention that I get a

sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.

message on boot.

---

### Post by curiousben on 2007-07-09
Still no luck guys. Really hoping somebody can help here. Please let me know if there's any other pieces of info you need.

---

### Post by curiousben on 2007-07-12
So I managed to get this working by moving the NIC to a different pci slot and loading the driver module with a media=0x01 option. i.e.

$ ifdown eth0
$ rmmod 8139too
$ modprobe 8139too media=0x01
$ dhclient eth0


Now the problem is I don't want to have to do this every session. Does anyone know how I can get the module to load with the media option on boot? I tried creating /etc/modprobe.d/options with no luck.

---

### Post by kevdog on 2007-07-12
Im going to take a wild stab at this one (kind of fun), based on the man pages you could try:

Within /etc/modprobe.d

gksu gedit 8139too

install 8139too /sbin/modprobe --ignore-install 8139too media=0x01

Im really not sure about the --ignore-install flag.  So if this doesnt work I would remove it and try again.

Let me know if this works!

---

