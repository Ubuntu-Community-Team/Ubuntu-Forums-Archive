---
title: "Restore Grub after install on other hard disk damaged mbr"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by scott-ian on 2011-05-19
I decided to set up the pre alpha version of Ubuntu on the first partition of my second hard drive.  I installed Ubuntu 10.04 (to upgrade later) and when I restarted my computer, it would not boot.  It loaded a Grub Rescue prompt.  I then booted of the second hard drive, and started my OS from there.  Any ideas?  I am not exactly a beginner, but I posted in this section because my problem does not seem too difficult.

---

### Post by wildmanne39 on 2011-05-19
> **scott-ian said:**
> I decided to set up the pre alpha version of Ubuntu on the first partition of my second hard drive.  I installed Ubuntu 10.04 (to upgrade later) and when I restarted my computer, it would not boot.  It loaded a Grub Rescue prompt.  I then booted of the second hard drive, and started my OS from there.  Any ideas?  I am not exactly a beginner, but I posted in this section because my problem does not seem too difficult.
Hi, I found this it should help, it tells you how to fix grub errors toward the bottom of the page. [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by scott-ian on 2011-05-19
Thanks.  I used this command: "sudo grub-setup /dev/sda".
That recorded grub to the MBR and allowed me to boot Linux normally.

---

