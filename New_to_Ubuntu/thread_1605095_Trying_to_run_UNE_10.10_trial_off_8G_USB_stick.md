---
title: "Trying to run UNE 10.10 trial off 8G USB stick"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by CarolElaine on 2010-10-24
Help!

Total Ubuntu/Linux newbie here. 

I recently bought an HP 210-1180NR netbook and thought I'd give UNE 10.10 a try. I've followed the directions on [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download). The USB drive was created on a reformatted 8G flash drive using Universal USB Installer. I've changed the boot order in the BIOS to:

USB Diskette on Key/USB Hard Disk
USB CD/DVD ROM Drive
USB Floppy 
Notebook Hard Drive

But when I look at the System Configuration screen, there is no option for a USB Diskette on Key/USB Hard Disk to be enabled - just CD-ROM Boot (enabled, but I don't have one), Floppy Boot (same as CD-ROM Boot) and Internal Network Adapter Boot (which is disabled). And when I try to boot from the flash drive it comes up with a screen that reads - 

Intel(r) Pineview PCI Accelerated SVGA BIOS
Build Number 2001 PC 14.34 03/01/2010 02:34:31
DECOMPILATION OR DISASSEMBLY PROHIBITED
Copyright (C) 2000-2003 Intel Corp. All Rights Reserved

 - with a blinking cursor that doesn't seem to do anything when I hit Enter or ESC or the spacebar. I also held the shift key when trying to boot up, but no luck.

Is it just because there's no option for a USB Diskette on Key/USB Hard Disk to be enabled in BIOS? Is there something else I'm missing?

Thank you!

---

### Post by cariboo on 2010-10-25
Try the latest version of unetbootin for Windows available [here]("http://unetbootin.sourceforge.net/"), there have been problems with other image creation tools, due to the newer version of syslinux that 10.10 uses.

---

### Post by C.S.Cameron on 2010-10-25
See if your flash drive is listed in BIOS as a hard drive, if so , select it as first hard drive.

---

### Post by CarolElaine on 2010-10-25
> **cariboo907 said:**
> Try the latest version of unetbootin for Windows available [here]("http://unetbootin.sourceforge.net/"), there have been problems with other image creation tools, due to the newer version of syslinux that 10.10 uses.

That seems to have been the problem - it's booting up fine from the flash drive now.

Thank you!

---

### Post by OldAndTired on 2012-03-11
Trying to try.  Got the latest UNetbootin.  Used it to download Ubuntu 10.x.  Worked fine on my antique Thinkpad.  Trying it on my Acer Aspire One gives the noted PineView message.  Help!

---

### Post by laresistance2 on 2012-11-19
I have exactly the same problem with my netbook "ACER Aspire One"
I formatted Windows 7 Starter and now I can not do anything installed because I always have this error.
I tried with Ubuntu, MeeGo, Fedora, Linux Mint, ... on my USB.

Do you have a solution, please?

---

