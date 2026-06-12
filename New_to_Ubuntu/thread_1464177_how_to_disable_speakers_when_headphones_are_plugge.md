---
title: "how to disable speakers when headphones are plugged in"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by thomz92 on 2010-04-27
hi. here's the issue... I have a back and front audio port. I plug my speakers into the back one. I want the speakers to stop playing when i plug headphones into the front. Is this possible? or else is there some sort of switch i can use to change from speakers to headphones? any ideas would be appreciated

---

### Post by gordintoronto on 2010-04-28
This is almost certainly a hardware issue with your computer. On my computer, when I plug earphones in the front, the speakers connected at the back are physically disconnected from getting any juice.

You might have mentioned what brand and model of computer you have.

---

### Post by -humanaut- on 2010-04-28
Click on the preferences of your Audio settings and select the Headphone jack as viewable then click it that SHOULD solve your problems depending on your hardware.

---

### Post by thomz92 on 2010-04-28
> **-humanaut- said:**
> Click on the preferences of your Audio settings and select the Headphone jack as viewable then click it that SHOULD solve your problems depending on your hardware.

are these instructions for kubuntu or ubuntu? because i'm using ubuntu and i'm not finding those settings.

---

### Post by bnhrobotics on 2010-04-28
I have the same issue. It became an issue for me when I upgraded to 9.10 from 9.04. I have a Gigabyte motherboard.

---

### Post by LowSky on 2010-04-28
> **thomz92 said:**
> are these instructions for kubuntu or ubuntu? because i'm using ubuntu and i'm not finding those settings.

> **bnhrobotics said:**
> I have the same issue. It became an issue for me when I upgraded to 9.10 from 9.04. I have a Gigabyte motherboard.

Those instructions were for Ubuntu. Some chipsets have odd options tat don't always get set correctly but can be changed. To do so we need to know your proper hardware, not just the company that makes it.

please enter this command and post the data please.

```
lspci -v
```

thats an lower case L not a 1 or I

---

### Post by bnhrobotics on 2010-04-28
Ok, I'll do that when I can get home to my computer.

---

### Post by thomz92 on 2010-04-28
heres what i got for my computer:

```
thomas@thomas-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M800 Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: e0000000-efffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
	Subsystem: D-Link System Inc Device 1301
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at e000 [size=256]
	Memory at f6012000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Device 2300
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at e100 [size=256]
	Memory at f6010000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 80000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at e200 [size=8]
	I/O ports at e300 [size=4]
	I/O ports at e400 [size=8]
	I/O ports at e500 [size=4]
	I/O ports at e600 [size=16]
	I/O ports at e700 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at e900 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at ea00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at eb00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
	Subsystem: Biostar Microtech Int'l Corp Device 3206
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f6011000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Biostar Microtech Int'l Corp Device 8212
	Flags: medium devsel, IRQ 22
	I/O ports at ed00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

thomas@thomas-desktop:~$
```

and my motherboard is a biostar P4M80-M7 i believe

---

### Post by bnhrobotics on 2010-04-28
Mine:

```

00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
	Subsystem: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
	Flags: bus master, 66MHz, medium devsel, latency 32
	Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [RAID5 mode]
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 96, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Giga-byte Technology Device 4385
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 5002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fa00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Giga-byte Technology Device a102
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe028000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
	Subsystem: eVga.com. Corp. Device c959
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at de00 [size=256]
	Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Memory at fdff8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394


```

---

### Post by -humanaut- on 2010-04-28
ATI & VIA Tough hardware but can be worked around Do both of you get sound from your speakers and its just the Headphone Jacks that are causing problems correct?

---

### Post by bnhrobotics on 2010-04-28
I do get sound from my speakers. And continue to get sound from my speakers when my headphone jack is plugged in. I lost a lot of sound options when I upgraded to 9.10. Also, since the upgrade every time the sound turns on there is an audible popping noise. This will happen at the start of a video, or a song if the audio is just starting. In the case of notifications such as empathy or google chat, I just hear annoying popping and not the sound. I figured I would wait for 10.04 at this point and hope for a fix, and if not start looking into the reasons why.

---

### Post by lidex on 2010-04-28
> **thomz92 said:**
> heres what i got for my computer:

```


00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Biostar Microtech Int'l Corp Device 8212
	Flags: medium devsel, IRQ 22
	I/O ports at ed00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx


thomas@thomas-desktop:~$
```

and my motherboard is a biostar P4M80-M7 i believe

Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-via82xx ac97_quirk=swap_hp  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

