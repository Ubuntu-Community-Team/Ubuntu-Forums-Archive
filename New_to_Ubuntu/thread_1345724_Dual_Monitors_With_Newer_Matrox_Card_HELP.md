---
title: "Dual Monitors With Newer Matrox Card HELP?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by tuxman_ottawa on 2009-12-04
Hey everyone, 
 
Although I'm a Newbie to Ubuntu I've been using gentoo and redhat for years. I decided to try ubuntu because I heard that for a desktop environment it was a little easier to setup and I've been having issues with my old distro's so it was time for a change.
 
I have a fairly new Matrox M91XX card (low profile PCIE dual head card) which apperently doesn't use the normal matrox drivers. 
 
No matter what I have tried I cannot get it to work with both heads. Can anyone help ? Suggest a corse of action.. I've tried Ximerma and Xrandr, neither with any success. It is very possible I have config issues that are preventing it but I haven't been able to find where.
 
Any ideas/help would be greatly appreciated. 
 
Thanks

---

### Post by ukripper on 2009-12-04
may help [https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia)

---

### Post by tuxman_ottawa on 2009-12-04
It's a thought... however when I downloaded them and tried to compile them I got this..

========================================
   Matrox Linux Driver Install Script   
========================================

Installation package v1.4.5.2

Refreshing ld database
Installing mtx_drv.so ...
Installing v4l_drv.so ...
Messages are being logged in file /tmp/make.log,
this might take some time.

Compiling mtx.ko ...
ERROR: There has been an error compiling the kernel module. 
       A log file has been created in the file /tmp/make.log


the first 2 were fine but when it tried to compile the mtx.ko 

/home/dave/matrox/matroxdriver_mtx-x86_32-1.4.5.2/kernel/src/mtx_mem.c:271: error: too few arguments to function ‘agp_allocate_memory’
make[2]: *** [/home/dave/matrox/matroxdriver_mtx-x86_32-1.4.5.2/kernel/src/mtx_mem.o] Error 1
make[1]: *** [_module_/home/dave/matrox/matroxdriver_mtx-x86_32-1.4.5.2/kernel/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [default] Error 2
dave@dave-desktop:~$

---

### Post by CHaoSlayeR on 2009-12-12
That one looks like an API change in the kernel that matrox was not aware of.

For the M91xx series the current driver is version 1.1.1 beta. Did you take that one? Although it was tested with Ubuntu 9.04 the newer kernel in Karmic introduced a lot of changes in memory handling and similar things so that it is not unlikely that matrox have to come up with a new version written against the changed API.

As the BinaryDriverHowto already mentions: works if you have luck.

Sad that their efforts of also developing the free mga driver have stopped years ago.


Cheers,

C]-[aoZ

[EDIT]
Be sure to read this carefully:

[ftp://ftp.matrox.com/pub/mga/archive/linux/2009/readme-1.1.1.txt](ftp://ftp.matrox.com/pub/mga/archive/linux/2009/readme-1.1.1.txt)
[/EDIT]

---

