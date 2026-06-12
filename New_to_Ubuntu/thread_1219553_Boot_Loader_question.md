---
title: "Boot Loader question"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Deefex on 2009-07-21
ok, so i installed ubuntu's boot loader on the sda1 part of the drive where windows is on. i have 2 drives. i'm installing ubuntu on my 2nd drive. on the options for installing the boot loader. i knew i had to install on the 1st drive. where recovery is on? so it was sda, sda1 (recovery files), sda2 (where windows xp is on). i tried before and it didn't show on start up. i'm on linux now cause i installed it again. it's weird cause it went up to 86% when it was installing and then gnome started. i hope i don't have to do anything else. please help me. i'm not going to shut down ubuntu till i get this fixed. thanks.

---

### Post by keplerspeed on 2009-07-21
I whould simply do a default install on the second drive, let ubuntu handle where grub (the bootloader) is installed. Windows will be detected and added to the bootloader automatically.

---

### Post by bodhi.zazen on 2009-07-21
If you do not know what you are doing probably better to go with the defaults.

Which would install grub on yoru primary drive , sda , aka (hd0) in grub speak.

If your bios give you the option of which drive to boot from you could install to sdb (second hard drive) (hd1) in grub speak.

I can not tell from your post what you mean by running the gnome desktop, you know the system runs "live" and you need to run the installer to install Ubuntu ?

If in doubt, back up your data first and read and understand the installation instructions ;)

---

### Post by Deefex on 2009-07-21
yeah, i'm running the installer again from within gnome. i edited the partitions to make more space for ubuntu. but i made too much. but whatever. i hope it works. i only did partitions for "/", "/home" and swap.

---

### Post by Deefex on 2009-07-21
nope, when i started i didn't get a grub menu asking me which os to boot from. i think i'm going to give up on ubuntu and maybe try another dist. but i'm going to buy the book with the cd.

---

