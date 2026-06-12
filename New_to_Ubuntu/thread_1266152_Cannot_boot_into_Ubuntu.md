---
title: "Cannot boot into Ubuntu"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by SafetyScissors on 2009-09-14
I'm new to Ubuntu, and trying to dual boot Windows 7 and Ubuntu.  I've installed Ubuntu on a new partition on the C drive, however, when I restart my comp, Windows automatically loads, without ever giving me the option to boot into Ubuntu.  Do I need to set up the boot loader or something?

---

### Post by LowSky on 2009-09-14
Did you use Wubi?

---

### Post by ukripper on 2009-09-14
Boot into Ubuntu Live cd and restore grub - [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) or use supergrub disk. Your windows 7 install has messed up grub in MBR therefore, you can't see grub anymore.

---

