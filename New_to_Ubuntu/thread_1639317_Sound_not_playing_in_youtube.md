---
title: "Sound not playing in youtube"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by mustis81 on 2010-12-06
Video works but i dont get sound. Same thing happens when i stream video in general. Im sorry if this is noobish, im very new to linux.

EDIT: I cant get sound anywhere, even offline. Im using the latest version of vlc and when i ran it i didnt get any audio :/ Please help thanks!

---

### Post by oldmankit on 2010-12-06
Have you checked through this page?  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by mustis81 on 2010-12-07
I checked out that page but still cant get any audio. When i enter the command line "lspci -v | less" in terminal it doesnt show any sound card installed but when i switch to windows ( i have ubuntu dual booted ) audio works just fine.

---

### Post by khelben1979 on 2010-12-07
> **mustis81 said:**
> I checked out that page but still cant get any audio. When i enter the command line "lspci -v | less" in terminal it doesnt show any sound card installed but when i switch to windows ( i have ubuntu dual booted ) audio works just fine.

I suggest that you post the output of that command to this thread. If it does not report any sound chip/card, you don't have any sound chip/sound card in there except if it was connected by USB.

What's the model of your laptop or desktop pc?

---

### Post by mustis81 on 2010-12-23
Sorry this reply took so long. The output of the command in my previous post is as follows.


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

When i checked for sound devices in windows it said i have Realtek High Definition Audio Speakers. The driver name is RTKVHD64.sys if that helps too. Thank you in advance for any advice offered!

---

