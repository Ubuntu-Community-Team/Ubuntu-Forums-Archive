---
title: "acer aspire one no bootable device"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by antonio_ing on 2009-06-17
hi guys 

i brought a new acer aspire one ZG5 but i would like to install ubuntu 9.04 (even the Remix version). Unfortunately, after the installation by means of a 1GB USB stick, the installation went fine (except for a fatal error in grub) and i could see the desktop. After rebooting, there is the error in a black screen that says "No bootable device".

How can i solve this?

thanks in advance

---

### Post by ~sHyLoCk~ on 2009-06-17
> **antonio_ing said:**
> hi guys 

i brought a new acer aspire one ZG5 but i would like to install ubuntu 9.04 (even the Remix version). Unfortunately, after the installation by means of a 1GB USB stick, the installation went fine (except for a fatal error in grub) and i could see the desktop. After rebooting, there is the error in a black screen that says "No bootable device".

How can i solve this?

thanks in advance

Where did you install the grub bootloader?

---

### Post by snakeman21 on 2009-06-17
Yeah, that sounds like a bootloader issue. I have an Aspire One, and I'm running Jaunty just fine.  I was running Netbook Remix, but recently switched to the desktop version.  One thing I do remember about installing Netbook Remix is that you can't use USB Startup Disk Creator.  Download USB ImageWriter and use that.  I don't remember why, but Netbook Remix will not install correctly if you make the live USB with USB Startup Disk Creator.

---

### Post by ~sHyLoCk~ on 2009-06-17
You can try re-installing grub on your Hard disk. See if [this]("http://ubuntuforums.org/showthread.php?t=224351") helps!

---

### Post by YesSir on 2009-06-17
Did you change the boot order in BIOS? (Computer still trying to boot from your USB stick?)

---

### Post by snakeman21 on 2009-06-17
> **YesSir said:**
> Did you change the boot order in BIOS? (Computer still trying to boot from your USB stick?)

Boot order shouldn't make a difference, as long as the main HD is included in the list.  It will try to boot the first entry, and if that device isn't there, it will move on to the second choice, and so on.

---

### Post by antonio_ing on 2009-06-18
snakeman21, you were right. I used imagewriter and at the beginning the problem was the same. Then i realize that i was installing the system remix in an external SD card. Anyway yesterday i was installing xubuntu in the correct hard disk and the problem still was there. So imagewriter was the best choice. I have found also this solution in the forum.

thank you to everybody

---

