---
title: "Can't boot 10.04 (different problem than other thread)"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Seijaku on 2010-08-31
Hello! I'm relatively new in the Linux world but not new testing LiveCDs and different distros. I've downloaded kubuntu-10.04.1-desktop-i386.iso, checked the hash, and burned it.
Everything runs fine until I can't load the live cd with this message

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.quashfs) on //filesystem.squashfs

after all of that, I get an empty prompt and can still run some commands.

Laptop specifications: Intel Pentium Dual Core T2080, 1GB RAM, motherboard L50IIX with Intel 945 chipset (very generic AFAIK)
Desktop specifications: Intel Core2Quad Q6600, Asus P5K Premium with Intel P35 chipset, 4gb ram (Supertalent DDR2-800 CAS5), VGA Asus 8800GT 1gb

To be honest, I'm totally and 100% clueless about this issue.

---

### Post by jtarin on 2010-08-31
Where did you download from?

---

### Post by jtarin on 2010-08-31
This seems to be not an uncommon problem with some laptops. Most have been solved by [placing the .iso image on a USB flash drive.]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by Seijaku on 2010-08-31
Thank you for your answer, jtarin. I downloaded it from the official site. I just tried Kubuntu DVD and it works flawlessly. But the LiveCD keeps giving me problems. I will try your solution! Thanks!

---

### Post by jtarin on 2010-08-31
You can alternately install Kubuntu and if you decide you don't like it you can the download and install Gnome and then either remove KDE or keep it and have the choice to run either desktop.

---

