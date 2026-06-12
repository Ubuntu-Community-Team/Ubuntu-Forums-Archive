---
title: "A Query of the Position of the Bootloader when Dual-booting 10.10 / Windows 7"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Andavane on 2010-10-12
This is a question supplementary to an earlier thread:

[http://ubuntuforums.org/showthread.php?t=1533756]("http://ubuntuforums.org/showthread.php?t=1533756")

From that friend I already installed Ubuntu 10.04 inside Windows itself using wubi, with good success. Now using yesterday's release, Ubuntu 10.10, I want to install this alongside Windows 7, instead of running inside it.

I have cleared the space for it, about 146 GB partition formatted to ext4, and Windows has been running fine, as well as the Ubuntu 10.04, into which I usually boot.

Now during the dual-boot installation, I was presented with the following, with the default choice being the first:

>  Boot loader
  Device for boot loader installation:

/dev/sda ATA Hitachi HT572323 (320.1 GB)
/dev/sda1 Windows 7 (loader)
/dev/sda2 Windows 7 (loader)
/dev/sda4
/dev/sda3 

It will install on sda4.

I presume the first option is where it will put the GRUB.
Am I correct before I proceed?

I want to understand a bit about what is going on first.
Will the GRUB clash with the Windows bootloader?
I haven;t proceeded yet!

Any comments gratefully appreciated

(Ubuntu 10.10 running on another machine and looking good!)

---

### Post by Chesamo on 2010-10-12
Just a question... you shouldn't have two partitions for the Win7 bootloader, only one. Why do you have two?

---

### Post by cariboo on 2010-10-12
Grub should be installed to the mbr of the first hard drive, which in your case is /dev/sda. do not install it to one of the partitions, as you could potentially damage something.

---

