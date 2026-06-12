---
title: "Dual booting ubuntu with windows7?"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by bobbrock on 2011-05-13
Hi everybody.
Im new to ubuntu I downloaded the live cd 11.04 about a week ago and used it twice
and know i want to installed it in computer tha allready haves windows7.
I allready made a partition for ubuntu through disk management .
I been reading this .[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) 
 And this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
If Any one haves any suggestions to help me with this task I would 
really appreciated.

Thank u

---

### Post by rez182 on 2011-05-13
make the partition you made for linux, unallocated, (use EASEUS patition master FREE) then simply select install ubuntu along side windows, and it will automatically create a separate swap space the same size as your RAM. and make sure you download all updates while installation. after the setup, if your computer loads normally, it means your laptop, specially your graphics card is compatible with the new 11.04 unity. unfortunately mine wasn't and my graphics card is nvidia gforce 310M.

---

### Post by astex on 2011-05-13
Both of those tutorials should work wonderfully.  When I use a system with several OSes installed, I tend to keep my media files on a windows partition and symbolic link my media folders in ~ to them.  This way there is no need for Windows to mount an ext3 or reiserfs partition, but your files remain available in every operating system.

Enjoy your new Ubuntu install.

---

### Post by Mark Phelps on 2011-05-14
An important safeguard to have in Win7 dual-boot situations is a Win7 Repair CD.  You can make your own by booting into Win7, selecting the Backup option, and selecting the option there to create and burn a Win7 Repair CD.

This will prove invaluable later, should you need to repair your Win7 boot loader.

---

