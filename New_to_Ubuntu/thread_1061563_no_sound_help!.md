---
title: "no sound help!"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-02-05
I installed Xubuntu 8.04 into this computer dual booting with Win98 a week ago.  Tried following a number of threads in the forums but still cannot get any sound at all.  The sound works ok on the Win98 side.

Here is output from aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

output from lspci -v
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
	Flags: bus master, medium devsel, latency 64
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: e2000000-e2dfffff
	Prefetchable memory behind bridge: e2f00000-e3ffffff

00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at d800 [size=16]

00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 12
	I/O ports at d400 [size=32]

00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
	Flags: medium devsel, IRQ 9

00:09.0 Multimedia audio controller: Creative Labs Ectiva EV1938
	Subsystem: Creative Labs Unknown device 5938
	Flags: bus master, slow devsel, latency 64, IRQ 12
	I/O ports at d000 [size=64]
	I/O ports at b800 [size=32]
	Capabilities: <access denied>

00:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Netgear FA310TX
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at b400 [size=256]
	Memory at e1800000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 10000000 [disabled] [size=256K]

01:00.0 VGA compatible controller: Intel Corporation 82740 (i740) AGP Graphics Accelerator (rev 21) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
	Memory at e3000000 (32-bit, prefetchable) [size=16M]
	Memory at e2000000 (32-bit, non-prefetchable) [size=512K]
	Expansion ROM at e2fc0000 [disabled] [size=256K]
	Capabilities: <access denied>

```

The soundcard appears to be Ensoniq with driver es1371
However I cannot find es1371 only ens1371 , is there much difference
I have put this into /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
snd-ens1371
snd-card-ens1371

```

I have checked the alsamixer and everything is on max and not muted.

still no sound.
Any ideas?

May be I need to use OSS but how do I change this in Xubuntu?
Thanks in advance.

---

