---
title: "Sound not working in 10.04"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by zaivala on 2010-05-03
I reported a few days ago that I had "upgraded" a working 9.10 machine to a totally dead (as far as booting goes) 10.04 system, losing all my personal files (99% of which are backed up on a Windows machine and/or an external hard drive).

Today I got my 9.10 disk out and reinstalled that.  After determining that everything was all right (except I didn't check the sound), I got really, really brave and started the upgrade again.

It took a while (although the download was much faster than it was the other day), but 3 hours later, I have an almost-working 10.04 system.

Almost.  No sound.  I probably should know how to fix and/or troubleshoot this, but I don't.  Any help?

For those wondering, I have a 2.2 GHz P4 Gateway E-6100.  Pretty solid, has worked well.  More specs to be revealed as requested.

---

### Post by GSF1200S on 2010-05-03
> **zaivala said:**
> I reported a few days ago that I had "upgraded" a working 9.10 machine to a totally dead (as far as booting goes) 10.04 system, losing all my personal files (99% of which are backed up on a Windows machine and/or an external hard drive).

Today I got my 9.10 disk out and reinstalled that.  After determining that everything was all right (except I didn't check the sound), I got really, really brave and started the upgrade again.

It took a while (although the download was much faster than it was the other day), but 3 hours later, I have an almost-working 10.04 system.

Almost.  No sound.  I probably should know how to fix and/or troubleshoot this, but I don't.  Any help?

For those wondering, I have a 2.2 GHz P4 Gateway E-6100.  Pretty solid, has worked well.  More specs to be revealed as requested.

What do you see available in System>Preferences>Sound>Output?

Can you give us the printout from the following commands:
```
uname -a
lspci -v
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by utnubuuser on 2010-05-03
Check and make sure sound isn't muted.
> alsamixer-look for MM, meaning muted.

---

### Post by nishant.singh28 on 2010-05-03
Ummm...try deleting the .pulse folder in your home folder and restart pusleaudio by issuing 
```

killall pulseaudio

```
That had helped me once when I'd reinstalled Karmic and had left my Home Partition untouched. Doing the above brought back audio.

---

### Post by zaivala on 2010-05-03
> **GSF1200S said:**
> What do you see available in System>Preferences>Sound>Output?

5880B [Audio PCI] Analog Stereo

> **GSF1200S said:**
> Can you give us the printout from the following commands:
```
uname -a
lspci -v
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

zaivala@zaivala-desktop:~$ uname -a
Linux zaivala-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

=====

zaivala@zaivala-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation 82875P/E7210 Memory Controller Hub
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: i82875p_edac, intel-agp

00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fc900000-fe9fffff
	Prefetchable memory behind bridge: e4800000-f47fffff
	Kernel modules: shpchp

00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fea00000-feafffff
	Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 60000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at ec00 [size=8]
	I/O ports at e800 [size=4]
	I/O ports at e400 [size=8]
	I/O ports at e000 [size=4]
	I/O ports at dc00 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Gateway 2000 Device 2023
	Flags: medium devsel, IRQ 3
	I/O ports at c800 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
	Subsystem: Micro-Star International Co., Ltd. Device 839c
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at fe9f0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-96, nvidiafb, rivafb, nouveau

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
	Subsystem: Gateway 2000 Device 2023
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	Memory at feae0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at ac00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000
	Kernel modules: e1000

03:03.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 04)
	Subsystem: Ensoniq Device 2000
	Flags: bus master, slow devsel, latency 32, IRQ 19
	I/O ports at bc00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

=====

zaivala@zaivala-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

=====

zaivala@zaivala-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

=====

zaivala@zaivala-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

I'm guessing that last one is the kicker.

Moss

---

### Post by zaivala on 2010-05-03
> **nishant.singh28 said:**
> Ummm...try deleting the .pulse folder in your home folder and restart pusleaudio by issuing 
```

killall pulseaudio

```
That had helped me once when I'd reinstalled Karmic and had left my Home Partition untouched. Doing the above brought back audio.

I just tried that.  No response, no relief.  Hope doing that doesn't kill the fixes from the result of the previous message.

---

### Post by zaivala on 2010-05-03
A member of WNCLUG asked me for this result:

zaivala@zaivala-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zaivala@zaivala-desktop:~$ 

Does that help anyone?

---

### Post by zaivala on 2010-05-04
As happens all too often in my questions about something not working, this time, again, there was a short circuit between the chair and the keyboard.

I checked what port the speakers were plugged into.  They were in the Line In port.  Oops.

However, and this should be another topic, my keyboard is still not being recognized every now and then.  Rebooting seems to fix it.

---

