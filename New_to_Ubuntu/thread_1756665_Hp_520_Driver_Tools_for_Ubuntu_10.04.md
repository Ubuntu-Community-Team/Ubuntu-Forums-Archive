---
title: "Hp 520 Driver Tools for Ubuntu 10.04"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by Alive_d_noob on 2011-05-12
Hi..
 
I have installed Ubuntu 10.04 on my laptop, model no. HP-520. Sadly i am unable to find any driver tools for Ubuntu 10.04. Please Help! I really want to Keep the Ubuntu OS as it is very good looking. I have Intel Celeron M CPU 440 @ 1.86 GHz Processor. Mobile Intel Express Chipset Family.
 
Please Help! It will be highly appreciated!!
 
P.S- The priority is the Ethernet Network Adapter Driver.

---

### Post by astex on 2011-05-12
Please copy and paste the output of

```
 $ lspci 
```

This is a brief list of your hardware and shows exactly what drivers will need to be installed.

---

### Post by Alive_d_noob on 2011-05-13
[FONT=Courier New][SIZE=3]ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] [/SIZE][/FONT]
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3]@astex : Hope this is helpful!!! :S[/SIZE]


[/FONT]

---

### Post by Alive_d_noob on 2011-05-13
HI
I found a file named "e100-3.5.17.tar" that can solve my problems. But being a absolute noob, I know nothing about how to run a .tar file in Ubuntu. So please tell me how to run & install this file in Ubuntu 10.04.
 
This file contains a src file, e100.7,e100.spec,ldistrib.txt,license,readme,sums.
 
The src file contains e100.c,ethtool.c,kcompat.h,Makefile.
 
Please tell while file to run, from where and by giving what commands.
 
Help will be highly appreciated. Thank you!! :D

---

### Post by astex on 2011-05-13
What you have actually downloaded is the source code of the driver (kernel module) you need.  Since the authors were kind enough to include a makefile, this should be relatively simple to use.  In terminal:

```
$ cd Downloads
$ tar -xf e100-3.5.17.tar
$ cd e100-3.5.17/src
$ make
$ sudo make install 
```

---

