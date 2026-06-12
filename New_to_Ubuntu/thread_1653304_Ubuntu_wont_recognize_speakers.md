---
title: "Ubuntu wont recognize speakers"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by mustis81 on 2010-12-26
I get audio just fine when i use headphones but noting through the speakers. I have ubuntu dual booted with windows 7 and get audio just fine on the windows side. Anybody know how to get my speakers to work in ubuntu?

P.S. The speakers are listed as Realtek High Definition Audio

---

### Post by Merk42 on 2010-12-26
> **mustis81 said:**
> I get audio just fine when i use headphones but noting through the speakers. I have ubuntu dual booted with windows 7 and get audio just fine on the windows side. Anybody know how to get my speakers to work in ubuntu?

P.S. The speakers are listed as Realtek High Definition Audio
What kind of computer is it?
Are you using the same jack for the headphones as you are the speakers?

With the speakers plugged in, try going to System > Preferences > Sound. Once there check the output tab and see if there are multiple options there to choose from.

---

### Post by Robing Goodfellow on 2010-12-26
I'm having the same problem, but with Altec Lansing speakers.  I lost the volume control icon in the notification area when I was toying around with Amarok, which I shortly thereafter uninstalled.  Not long after that I lost my speakers.   Mine is an HP G62-367DX Laptop.

regards, RG

---

### Post by mustis81 on 2010-12-26
The computer is an hp G62-234DX notebook and the speakers are internal. And the output menu in sound preferences only has one option, Internal Audio Analog Stereo.

---

### Post by mustis81 on 2011-01-01
When i enter the command line "lspci -v | less" in terminal, the output is as follows:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 33
Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
I/O ports at 4050 [size=8]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at d4406100 (64-bit, non-prefetchable) [size=16]
:


I heard somewhere that entering this line will help but i never got any follow up when i asked what it all meant lol. Still cant get audio, can someone please tell me if they see the problem above? Thank you.

---

### Post by sandyd on 2011-01-01
> **mustis81 said:**
> When i enter the command line "lspci -v | less" in terminal, the output is as follows:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 33
Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
I/O ports at 4050 [size=8]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at d4406100 (64-bit, non-prefetchable) [size=16]
:


I heard somewhere that entering this line will help but i never got any follow up when i asked what it all meant lol. Still cant get audio, can someone please tell me if they see the problem above? Thank you.
post output of
```

aplay -l
```

---

### Post by mustis81 on 2011-01-01
output of aplay -l is:


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by sandyd on 2011-01-01
> **mustis81 said:**
> output of aplay -l is:


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
you sure your plugging it into the right jack?
theirs several other computers with the same card, and it works fine, other than this dude [http://art.ubuntuforums.org/showthread.php?p=9851480](http://art.ubuntuforums.org/showthread.php?p=9851480)

---

### Post by riverpirate on 2011-01-07
Im having the exact same problem with the hp g62. my audio on my headphone line will work, but the built in speakers will not. Ive gone into system preferences and everything seems to be in check. Help would be greatly appreciated.

---

### Post by b0b138 on 2011-01-07
[http://ubuntuforums.org/showthread.php?t=1528275](http://ubuntuforums.org/showthread.php?t=1528275)

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

