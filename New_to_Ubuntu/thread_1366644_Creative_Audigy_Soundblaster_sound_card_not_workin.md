---
title: "Creative Audigy Soundblaster sound card not working"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Suse on 2009-12-28
Hi,

I'm very new to Ubuntu, having finally taken the leap yesterday to install it. ):P  All is going well (I think!), except that I can't get the sound to work. This is a brand new install, not an upgrade. No sound problems in XP, just Ubuntu. The version is Karmic Koala 9.10.

I've only started learning the terminal, so I'm not at all sure what I'm doing yet regarding commands. I've followed a few how to solve sound problem tips from the forums, but I'm getting nowhere. 

Can anyone help? 

No idea if this info will be useful, but here goes:


susan@susan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
...

  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0

...

  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
susan@susan-desktop:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bf
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-0000bfff
	Memory behind bridge: bfe00000-dfefffff
	Prefetchable memory behind bridge: 000000009fd00000-00000000bfcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at dffbe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at dffbfc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e000 [size=16]
	Memory at dffbd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation Device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at dffb8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 816a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at dffbc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at dc00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

03:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
	Subsystem: ASUSTeK Computer Inc. Device 0152
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at b000 [size=256]
	Expansion ROM at dfee0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon

03:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
	Subsystem: ASUSTeK Computer Inc. Device 0153
	Flags: bus master, fast devsel, latency 0
	Memory at c8000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

04:09.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 1021
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at cc00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

susan@susan-desktop:~$

---

### Post by kostkon on 2009-12-28
First of all, did you try to setup your sound in *System &#8594; Preferences &#8594; Sound*?

---

### Post by Suse on 2009-12-28
Hi

Yes. Nothing is muted, and I've turned everything up full. My sound card shows under hardware as SB0400 Audigy2 Value, and I've tried selecting quite a few of the many settings, without knowing what I'm doing to be honest.

---

### Post by kostkon on 2009-12-28
OK. You may need to turn off (or turn on, depending of your setup) the *Analog/Digital* hardware switch of your card.

Check [here]("http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html") for a way to accomplish this.

---

### Post by Suse on 2009-12-28
I've actually tried that one. Unfortunately it doesn't make a difference.

---

### Post by kostkon on 2009-12-28
Did you check the levels of your hardware volumes in gnome-alsamixer?

---

### Post by kostkon on 2009-12-28
Also did you try all the available profiles in the *Hardware* tab of your sound prefs (i.e. System &#8594; Preferences &#8594; Sound)?

---

### Post by Suse on 2009-12-28
It's fixed! I just about jumped out my skin at the volume. Under Hardware in Sound Preferences, I clicked through all of the Sound Blaster options. Turns out I needed to set it to Internal Audio instead, profile Analogue Stereo Output. I'm not convinced it's quite right, as You Tube sounds shocking. The sounds breaks up terribly. But I will experiment some more.

Thank you.

---

