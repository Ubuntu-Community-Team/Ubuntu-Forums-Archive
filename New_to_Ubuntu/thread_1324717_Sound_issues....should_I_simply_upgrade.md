---
title: "Sound issues....should I simply upgrade?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-12
Hi, I am slowly ticking my issues away. First I was unable to play flash but I solved that, with lots of help here!

My other major issue is that I am unable to play or hear any sound at all.

If I try Advanced Linux Sound Architecture - and do Test Pipe - nothing at all happens. I have tried so many things and the advice here although excellent can seem tricky to follow.

If I simply upgrade from 8.10 to the latest version, you reckon that might seek and correct my sound nightmare? :o

---

### Post by camaron1 on 2009-11-12
> **listerdl said:**
> Hi, I am slowly ticking my issues away. First I was unable to play flash but I solved that, with lots of help here!

My other major issue is that I am unable to play or hear any sound at all.

If I try Advanced Linux Sound Architecture - and do Test Pipe - nothing at all happens. I have tried so many things and the advice here although excellent can seem tricky to follow.

If I simply upgrade from 8.10 to the latest version, you reckon that might seek and correct my sound nightmare? :o

Sound can be a complicated thing in linux (my own experience)
Look at these two very good threads if you haven't yet:

 [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I wouldn't just upgrade to solve that problem as it can be a lot of hassle, can cause other issues and of course not solve your problem.

---

### Post by Aetixintro on 2009-11-12
Hello
I've just upgraded to 9.10 and I've had problems with Movieplayer sound, but now everything works beautifully! I can only recommend the Karmic!

(Btw, the system has also been slowing down earlier, but now that also flows as it should!)

---

### Post by camaron1 on 2009-11-12
> **Aetixintro said:**
> Hello
I've just upgraded to 9.10 and I've had problems with Movieplayer sound, but now everything works beautifully! I can only recommend the Karmic!

(Btw, the system has also been slowing down earlier, but now that also flows as it should!)

I'm glad for you, but Karmic has broken the sound to many people, just look at the forums. (I was one of the unfortunates)

---

### Post by mr clark25 on 2009-11-12
i uninstalled pulseadio and that fixed my problem with the sound.

 i just lost the volume control at the top of the screen (the volume is stuck at max). that was just fine for me because i have volume control on my speakers.

---

### Post by listerdl on 2009-11-13
OK, I am determined to get sound but trust me, this is really taking a lot of time....

Following this tutorial: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I am trying to identify my sound card by typing this into terminal:

```
lspci -v
```

This is the output - I assume that the first paragraph is my soundcard?

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 92080000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0022
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ffc80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at cff8 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at ffc40000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0022
	Flags: fast devsel
	Memory at 92000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ff900000-ff9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ff800000-ff8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at afe0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at af80 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at af60 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at af40 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffc3fc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 8c000000-91ffffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 221
	I/O ports at af38 [size=8]
	I/O ports at af34 [size=4]
	I/O ports at af28 [size=8]
	I/O ports at af24 [size=4]
	I/O ports at af10 [size=16]
	Memory at ffc3f800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at ff9e0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at bfe0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at ff8fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at 90004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at 90005000 (32-bit, non-prefetchable) [size=2K]
	Memory at 90000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at 90005800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```


Now, the the next step after identifying my soundcard is...

".........Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).........."

ok, im not too sure what to do here since I am not sure what my soundcard is? 

Thanks for all replies - i have honestly tried at least 50 different things and am a little worried that i have completed screwed up the sound settings....(is that possible?!)

---

### Post by listerdl on 2009-11-13
Also, not sure if this helps but when I tried the Sounds Events Sound Playback ASLA Pipe Test this info came up: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

Does that help at all?

---

### Post by nothingspecial on 2009-11-13
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

That is your soundcard

---

