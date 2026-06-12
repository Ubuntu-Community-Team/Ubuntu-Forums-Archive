---
title: "Grub Error 2"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by B34ST1Y on 2009-06-10
Hi all,


I couldn't seem to crop up a clear answer by searching around the internet. 


I just "successfully" installed Ubuntu 9.04 (64-bit) onto my computer. I have a software RAID 0 setup running. During the install, the installer correctly identified my 640 gB partition (2 320's striped together) and didn't have any apparent errors during the installation, however....when I rebooted my computer after the install to use my new OS, it didn't load past grub with "Grub Error 2" message.


Does anyone know what this is, and how I could possibly fix it?

---

### Post by ronparent on 2009-06-13
In many, but not all, instances of 9.04 on raid0, the raid drives are not active when fstab is acted on. In these cases the grub bootloader cannot find grubs stage1 and stage2 in /boot/grub. Both can be affected. The work around has been reported on the server forum for the software raid.

---

### Post by Bucky Ball on 2009-06-13
[http://members.iinet.net.au/~herman546/p15.html#2_]("http://members.iinet.net.au/%7Eherman546/p15.html#2_")

Check that ...

---

