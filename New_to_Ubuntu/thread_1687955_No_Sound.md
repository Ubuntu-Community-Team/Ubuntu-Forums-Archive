---
title: "No Sound"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by Aoude on 2011-02-14
I just installed Ubuntu 10.04 and I have no sound.
I have checked and headphones do work(BARELY AUDIBLE), however the laptop speakers do not.

[RIGHT]Thanks, Aoude
[/RIGHT]

---

### Post by grahammechanical on 2011-02-14
What have you tried to do to fix it? Do you notice the Sound icon? Left click it. Do you see the word Mute? Or do you see Unmute. If you see Unmute, then click it.

Also, on the System>Preferences menu you will see an entry called Sound. Select it. On the dialog box and on some of the tabs you will see a tick box labeled Mute. Make sure that none of them are ticked. You can also adjust the Output volume. Make sure that it is not set to the lower end of the scale.

Regards.

---

### Post by Aoude on 2011-02-14
Its showing all sound is not muted.

Also I have taken some screen shots.

[ATTACH]183496[/ATTACH]

[ATTACH]183497[/ATTACH]

[ATTACH]183498[/ATTACH]

[ATTACH]183499[/ATTACH]

[ATTACH]183500[/ATTACH]

I have also followed the steps here,

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

All of the general help, alsamixer, saving sound settings, and adding the current user to the audio group(audio:x:29:pulse:patrick).

---

### Post by navjeetsingh on 2011-02-14
I previously used ubuntu 8.04 and it was lovely. Finally , now i installed 10.10 but now sound doesn't work at all.

i hv checked the 'use sound devices' in the 'users and groups' window but that doesn't solve the issue.

I'm new to this and doesn't know much of ubuntu. so please detail the solution. 

For background info :

navjeet@navjeet-System-Product-Name:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Aoude on 2011-02-14
hmm, try following the guide I posted and if that doesn't work for you we may be stuck in the same boat :(

Similar to you I had 10.10 and I downgraded to 10.04 due to an issue, now I have no sound (note this was a clean format install). However sound did work fine on the Live CD of 10.04

---

### Post by Aoude on 2011-02-14
*note my card uses module snd-hda-intel

---

### Post by racie on 2011-02-14
There's a great audio troubleshooting page here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Worked great for me when my sound wasn't working.

---

### Post by Aoude on 2011-02-14
**lspci -v | less**


        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e0000000-f00fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f5e0a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at f5e08000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
[B]
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f5e00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel[/B]

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f4a00000-f5dfffff
:

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f3600000-f49fffff
        Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f2200000-f35fffff
        Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f0200000-f21fffff
        Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f5e07000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
:

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 35
        I/O ports at e070 [size=8]
        I/O ports at e060 [size=4]
        I/O ports at e050 [size=8]
        I/O ports at e040 [size=4]
        I/O ports at e020 [size=32]
        Memory at f5e06000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
        Subsystem: Sony Corporation Device 9071
        Flags: medium devsel, IRQ 4
        Memory at f5e05000 (64-bit, non-prefetchable) [size=256]
        I/O ports at e000 [size=32]
        Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at f5e04000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 36
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=256]
:

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0040000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Foxconn International, Inc. Device e017
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4a00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f3602000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at f3601000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f3600000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

:

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 34
        Memory at f2220000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Expansion ROM at f2200000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sky2
        Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0

(END) 


[http://www.alsa-project.org/db/?f=6ff1d49460d2ee794d6887747a1bc2a8221fa489]("http://www.alsa-project.org/db/?f=6ff1d49460d2ee794d6887747a1bc2a8221fa489")

---

### Post by Aoude on 2011-02-14
also i decided to check my headphones again and those are extremely quiet on max volume and are barely audible :confused:

---

### Post by gruffyddd on 2011-02-20
The sound from my sound-card went quiet about 2 weeks ago. I have not found a solution yet, but it may be to do with [this]("https://bugs.launchpad.net/ubuntu/+bug/708586").

---

