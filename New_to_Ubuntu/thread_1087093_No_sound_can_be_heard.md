---
title: "No sound can be heard"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Embryonic on 2009-03-04
Hello. I've been enjoying my Ubuntu, but I recently reinstalled it after trying the Win 7 Beta(It sucks). on this install  however I am having problems getting my sound to work. on my last install I had no problems at all with it.

Hardware is as follows

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Elitegroup Computer Systems Device 2140
	Flags: bus master, 66MHz, medium devsel, latency 64
	I/O ports at 4100 [disabled] [size=32]

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Elitegroup Computer Systems Device 1b34
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
	I/O ports at fe00 [size=8]
	I/O ports at fd00 [size=4]
	I/O ports at fc00 [size=8]
	I/O ports at fb00 [size=4]
	I/O ports at fa00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at f0000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil, pata_acpi, ata_generic

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Elitegroup Computer Systems Device 1b34
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at f900 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f700 [size=8]
	I/O ports at f600 [size=4]
	I/O ports at f500 [size=16]
	Memory at fe02e000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at f0080000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil, pata_acpi, ata_generic

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 2140
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 2140
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 2140
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Elitegroup Computer Systems Device 1b34
	Flags: 66MHz, medium devsel
	I/O ports at 0400 [size=16]
	Memory at fe02a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Device 2140
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f300 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp, pata_acpi, ata_generic

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Elitegroup Computer Systems Device 1b34
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fde00000-fdefffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
	Subsystem: Elitegroup Computer Systems Device 1877
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
	Subsystem: XFX Pine Group Inc. Device 2286
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=512M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at df00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Elitegroup Computer Systems Device 8139
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at dc00 [size=256]
	Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too
```

I would like to have the sound going thru my Soundblaster (which is how I had it before, with no problems) Any help would be great
Thanks in advance!

Embryonic

P.S. I'm using Intrepid Ibex (8.10)

---

### Post by neppakyo on 2009-03-04
one option is to remove pulseaudio and stick with plain alsa >.>

---

### Post by Embryonic on 2009-03-04
I don't have Pulseaudio...

---

### Post by neppakyo on 2009-03-04
unless you manually remove it, its installed by default.

---

### Post by Embryonic on 2009-03-04
Well how would I go about removing it then? I don't see an installed version in my add/remove programs list. Sorry for the question, but I'm pretty new to linux here and am not sure about how to go about removing stuff if its not in that list

---

### Post by Therion on 2009-03-04
Not sure but it *looks* as if you've not yet disabled the onboard audio chipset (the AC'97 Audio Controller).  Since you've installed your Soundblaster soundcard the on-board audio should be disabled in the BIOS to prevent system-wide audio borkage.

Second thing to check is under Volume/properties.  Do you have a "Switches" tab?  If so, see if there's a tic box for the **Audigy Digial Input/Output Jack**.  
If there is, see if clearing that tic-box (or tic'ing the box "on" if it's off) has any effect on restoring your sound.

---

### Post by Embryonic on 2009-03-04
Wow, I can't believe I forgot to disable my on board sound. (thought I had done that a year ago when I upgraded the PC) Thanks much Therion!

---

### Post by neppakyo on 2009-03-04
> **Embryonic said:**
> Wow, I can't believe I forgot to disable my on board sound. (thought I had done that a year ago when I upgraded the PC) Thanks much Therion!

>.< I should read more carefully, and i would of noticed you wrote that. Would of been my first thing to say to shut off lol

---

### Post by Therion on 2009-03-04
> **Embryonic said:**
> Wow, I can't believe I forgot to disable my on board sound. (thought I had done that a year ago when I upgraded the PC) Thanks much Therion!
LOL... Happens to the best of us.  I had a GRUB error a couple weeks ago and some of my BIOS settings got set back to factory defaults.  Got my memory timings back, reconfigured the boot sequence, disabled all sorts of legacy this, legacy that...  But sound is borked.  Hard.  About a six-pack later it dawns on me.

Dozens of system builds under my belt and I forget to disable the on-board audio...  :P

---

