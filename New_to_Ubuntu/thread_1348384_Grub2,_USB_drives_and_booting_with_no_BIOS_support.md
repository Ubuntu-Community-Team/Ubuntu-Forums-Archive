---
title: "Grub2, USB drives and booting with no BIOS support"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by marvin_littlewood on 2009-12-07
Hello!

Apologies in advance if this has been asked and answered. Googling and searching the forums has lead to nothing that quite covers my situation and what is there, covers GRUB not GRUB2.

I have a Sony Vaio PCG GRT896SP laptop into which I put a new hard-disk and did an install of Ubuntu 9.10. Unfortunately it's BIOS (and upgrades) does not support boot from USB.

The old hard disk has a working copy of WinXP on it. I have put the old HD into a caddy and can use it as an USB drive.

I would prefer to boot into Ubuntu by default but for the rare occasions I want to use WinXP, can GRUB2 be persuaded to load sufficient USB functionality to see the drive, so that I can boot into Windows when the drive is plugged in?

Many thanks in advance

Marv

---

### Post by cariboo on 2009-12-11
Grub2 doesn't have the ability to boot from a usb drive, if the computer doesn't support it. There are boot disks available that will load the drivers needed to boot from a usb drive.

---

### Post by Mr. Wishes on 2009-12-14
It so happens I'm having the same problem at the moment.

[This thread]("http://ubuntuforums.org/showthread.php?t=992426") suggests that one way is to use grub to load a kernel that can then access the usb disk and run from there. Unfortunately, the guide is for grub, not grub2, but I expect it would work with appropriate modifications in grub2. I've never played around with the grub2 configuration files before though, so I'm not sure what those modifications would entail.

In my particular case, I have grub2 and ubuntu 9.10 installed on a very slow/unstable internal hdd, and I'm planning to try to boot off an external hdd with ubuntu 8.10, even though I have no BIOS USB support. This means I don't have to worry about chainloading Windows or anything. To be honest, I don't find Windows very good for fancy booting, so I doubt the original poster will succeed, though I wish him luck.

I'm going to see what I can do and I'll let you know how I go. If anyone has any advice or any reason why this won't work, do please let me know.

---

### Post by Mr. Wishes on 2009-12-20
I said I'd let you know how I went, but I decided to just get a new laptop instead. Good luck!

---

