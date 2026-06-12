---
title: "mmc0 unknown controller - you may experience problems"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by al.adab on 2010-05-05
hello,

I installed Ubuntu 10.04 on a Dell Vostro 1310. The booting process was really fast, and all I noticed was a couple of black screens before getting to the desktop. 

On a fresh installation (due to some issues), it takes much longer for Ubuntu to load. Besides, before getting to the desktop, I notice that the cursor blinks for some 20secs, and a message (very briefly) appears: 

"unknown controller - you may experience problems" (I don't know if it says exactly this as it disappear very quickly). 

do you know what this is all about?

---

### Post by al.adab on 2010-05-05
just come across

[https://bugs.launchpad.net/ubuntu/+bug/323159](https://bugs.launchpad.net/ubuntu/+bug/323159)

where it is suggested to edit */etc/modprobe.d/blacklist.conf*
and insert the following

[I]blacklist sdhci-pci
blacklist sdhci
blacklist mmc_core[/I]

whatever this is about, the message is now gone, and the cursor doesn't blink as long as before. A message comes out right before the desktop appears, but I don't manage to pause it to read it (any suggestion how to do this on a Dell Vostro 1310 keyboard? I thought it's enough to hit "pause"...). 

More on this message as soon as I've figured out how to read that message.

---

### Post by bjordan1979 on 2010-06-01
I have the same issue running 10.04. I have all the current updates and the install was a clean install not upgrade.

Kernel version:

Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed 

On boot I see a blinking cursor for a while the error blips up on the screen then the boot splash screen starts. My kern.log has:

------------------------------------------
Jun  1 19:40:59 Workstation20 kernel: [   14.158573] sdhci: Secure Digital Host Controller Interface driver
Jun  1 19:40:59 Workstation20 kernel: [   14.158577] sdhci: Copyright(c) Pierre Ossman
Jun  1 19:40:59 Workstation20 kernel: [   14.160559] sdhci-pci 0000:03:05.2: SDHCI controller found [1217:7120] (rev 1)
Jun  1 19:40:59 Workstation20 kernel: [   14.160583] sdhci-pci 0000:03:05.2: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
**Jun  1 19:40:59 Workstation20 kernel: [   14.160617] mmc0: Unknown controller version (16). You may experience problems.**
Jun  1 19:40:59 Workstation20 kernel: [   14.160723] Registered led device: mmc0::
Jun  1 19:40:59 Workstation20 kernel: [   14.160778] mmc0: SDHCI controller on PCI [0000:03:05.2] using PIO
------------------------------------------

My card reader still works correctly. I recently copied images from an SD card.

I'm on an Averatec 2300 series notebook.

I'd love to resolve the issue. More importantly find a way to speed up my boot times. It probably sits on the blinking cursor for about 15 seconds (maybe more). Which is really annoying on boot.

---

### Post by johnathanamber on 2010-07-14
I am also having this issue. I have this thread going:
[http://ubuntuforums.org/showthread.php?p=9590058#post9590058](http://ubuntuforums.org/showthread.php?p=9590058#post9590058)

Problem with the blacklist thing is that I was to use my card reader. That would block it form being used.

God bless,
Johnathan

---

### Post by Aeric on 2010-08-01
> Aug  1 14:59:47 Ubuntu kernel: [   22.151942] acer-wmi: Brightness must be controlled by generic video driver
Aug  1 14:59:47 Ubuntu kernel: [   22.156922] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Aug  1 14:59:47 Ubuntu kernel: [   22.172921] sdhci: Secure Digital Host Controller Interface driver
Aug  1 14:59:47 Ubuntu kernel: [   22.172924] sdhci: Copyright(c) Pierre Ossman
Aug  1 14:59:47 Ubuntu kernel: [   22.174435] sdhci-pci 0000:0f:06.2: SDHCI controller found [1217:7120] (rev 2)
Aug  1 14:59:47 Ubuntu kernel: [   22.174459] sdhci-pci 0000:0f:06.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
**Aug  1 14:59:47 Ubuntu kernel: [   22.174485] mmc0: Unknown controller version (2). You may experience problems.**
Aug  1 14:59:47 Ubuntu kernel: [   22.174571] Registered led device: mmc0::
Aug  1 14:59:47 Ubuntu kernel: [   22.174611] mmc0: SDHCI controller on PCI [0000:0f:06.2] using DMA
I guess mmc0 is something related to multimedia controller?

---

### Post by akoskm on 2010-08-01
> **Aeric said:**
> I guess mmc0 is something related to multimedia controller?

As mentioned above it is the card reader, (M)ulti (M)edia (C)ard.

---

