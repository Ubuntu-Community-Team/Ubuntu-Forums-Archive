---
title: "ERROR 15 on boot, how to edit grub.cfg?  Files are read only"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-11-01
Hi, I am getting an ERROR 15 on boot up on my dual boot system.  I got this after upgrading to grub2.   I can boot off the CD and I can see the grub.cg file, but I can't edit it as the partition is read only when booting from the CD.

How to I enable editing of my files on the hard disk?

A related question will be regarding what I need to do to correct my grub.cfg file, but we're not there yet!

---

### Post by 0cton on 2009-11-01
you may need to open it with root privileges (sudo gedit for example)

---

### Post by gatorbrit on 2009-11-01
Yeah, i thought that might be it, but from the CD it just goes sudo without asking me a password.   I guess I need to "login" to the other partition on the HD.

---

### Post by coffeecat on 2009-11-01
> **0cton said:**
> you may need to open it with root privileges (sudo gedit for example)

Indeed, but it should be "gksudo gedit".

@gatobrit, have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) . That link will tell you all you need to know about getting administrative privileges in Ubuntu.

> **gatorbrit said:**
> A related question will be regarding what I need to do to correct my grub.cfg file, but we're not there yet!

**Do not** directly edit your grub.cfg file. Grub 2 is more complicated to configure than legacy grub. Here are a couple of useful links:

Community documentation:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Forum thread, Grub 2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

