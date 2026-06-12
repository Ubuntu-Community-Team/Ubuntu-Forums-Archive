---
title: "Older versions of Ubuntu and sound issues"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by bradwal on 2009-01-23
I've had Ubuntu for about a month now and I want to like it, I just can't get my sound to work myself and can't find any help to get it to work either. Does anyone know if there's a chance older versions of ubuntu could be more compatible for sound? I'd like to keep ubuntu but a computer without sound is almost useless to me so maybe there's hope out there with an older version.

---

### Post by Cypher on 2009-01-23
You're using 8.10 Intrepid Ibex? Sometimes removing pulseaudio and returning to ALSA will make sounds work again, so follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=973637") and see if that'll make things better for you.

The older versions of Ubuntu used ALSA/OSS more than Pulseaudio, and sound might indeed work, but then you're running out of dated software as far as everything else is concerned. So you're better of getting 8.10 happy with sound..

---

### Post by psychomichael on 2009-01-23
Some of us are still unable to get sound by removing Pulseaudio...and I don't want to move to Intrepid until all the bugs are worked out. I heard something that there was a possibility of rolling back the kernel?

---

### Post by LowSky on 2009-01-23
I have never had a sound issue on any of the 6 boxes I installed Ubuntu on. Could you guys please give your system specs so we can try to resolve this.

---

### Post by cwsnyder on 2009-01-23
Try using the instructions in this thread: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 
Comprehensive Sound Problem Solutions Guide v0.5e to remove and re-install your ALSA sound drivers.  That fixed my Intrepid sound problems which I had been having since I installed Intrepid Ibex back in November.

---

### Post by bradwal on 2009-01-23
> **Cypher said:**
> You're using 8.10 Intrepid Ibex? Sometimes removing pulseaudio and returning to ALSA will make sounds work again, so follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=973637") and see if that'll make things better for you.

The older versions of Ubuntu used ALSA/OSS more than Pulseaudio, and sound might indeed work, but then you're running out of dated software as far as everything else is concerned. So you're better of getting 8.10 happy with sound..

I haven't seen this thread for troubleshooting sound yet, I'll try it out.

> **LowSky said:**
> I have never had a sound issue on any of the 6 boxes I installed Ubuntu on. Could you guys please give your system specs so we can try to resolve this.

Here's my aplay from before I removed alsa -

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

here's my lspci after removal, I'll try reinstalling then editing this -

```
lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Device 203a
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Device 203a
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Device 203a
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Rioworks Device 203a
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Rioworks Device 203a
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 3
	Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: e0200000-e02fffff
	Prefetchable memory behind bridge: 30000000-37ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Memory at 38000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Rioworks Device 203a
	Flags: medium devsel, IRQ 10
	I/O ports at 1880 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Rioworks Device 2030
	Flags: medium devsel, IRQ 10
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 3c000000-3ffff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0203000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 40000000-43fff000
	I/O window 0: 00003c00-00003cff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01) (prog-if 10)
	Subsystem: Rioworks Device 203a
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0201000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Rioworks Device 202d
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at 3000 [size=256]
	Memory at e0201800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2701
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200
```


I'm running ubuntu on a Gateway 4520gz laptop- 512mb RAM, 60 gb hd, 1.5 GHz pentium M 



> **cwsnyder said:**
> Try using the instructions in this thread: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 
Comprehensive Sound Problem Solutions Guide v0.5e to remove and re-install your ALSA sound drivers.  That fixed my Intrepid sound problems which I had been having since I installed Intrepid Ibex back in November.

I've gone through the comprehensive sound problem solutions guide a few times but nothing's worked. I'll keep trying though, I don't really want to give up on ubuntu. I might try a complete reinstall of alsa and pulse. There's a little note at the bottom of that guide that goes to my system -

It says to get ac97 to work I need to edit /etc/modprobe.d/alsa-base and add this to the last line - "options snd-intel8x0 ac97_quirk=3". I might not of edited that right. Once I reinstall and it doesn't work I might post that for you guys to check if I did it right.

---

### Post by bradwal on 2009-01-23
I finally have system sounds, maybe I'm starting to get on the right track here.

---

### Post by bradwal on 2009-01-23
Cypher, I tried your suggestion and it didn't work. I've reinstalled Pulse audio since it seems like that may be the easiest way for it to get working

I've lost my system sounds now again though. I have no idea what my problem could be. I've made sure all my alsamixer channels are unmuted and went through the comprehensive sound guide, along with the "PulseAudio Fixes & System-Wide Equalizer Support" tutorial. I'll be on later tonight again trying to figure this out.

---

### Post by psychomichael on 2009-01-23
> **LowSky said:**
> I have never had a sound issue on any of the 6 boxes I installed Ubuntu on. Could you guys please give your system specs so we can try to resolve this.

Here's the thread where I've posted all of my specs...I should note that I'm not using Intrepid, still on Gutsy.

[http://ubuntuforums.org/showthread.php?t=1043254](http://ubuntuforums.org/showthread.php?t=1043254)

---

### Post by cariboo on 2009-01-23
@psychomichael:

Last weekend I spent a couple of hours trying to get the same sound card to work in Windows XP. It seems the manufacturer doesn't even support that chipset anymore,  they've had a notice on their website about licensing issues for about 6 months and no drivers available. I finally stuck an old soundblaster 16 in it and sound works in XP and with the LiveCD, it took less than 5 minutes to fix.

Jim

---

### Post by psychomichael on 2009-01-24
> **cariboo907 said:**
> @psychomichael:

Last weekend I spent a couple of hours trying to get the same sound card to work in Windows XP. It seems the manufacturer doesn't even support that chipset anymore,  they've had a notice on their website about licensing issues for about 6 months and no drivers available. I finally stuck an old soundblaster 16 in it and sound works in XP and with the LiveCD, it took less than 5 minutes to fix.

Jim

Yeah, but the real bummer is that this sound card worked great with 7.04 and for a long time with Gutsy. I'm still wondering if it has something to do with the kernel, but I haven't been able to figure out how to revert back to the old one.

---

### Post by bradwal on 2009-01-25
This is something I forgot to add - Could I maybe be having sound problems due to my Ubuntu being a dual boot with Windows? My sound isn't even working on Windows, it says another program is using the sound device.

---

