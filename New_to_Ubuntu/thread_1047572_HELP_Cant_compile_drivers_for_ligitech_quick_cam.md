---
title: "HELP Cant compile drivers for ligitech quick cam"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by annihilator89 on 2009-01-22
Hello,
I am currently using Kubuntu and I want to use my logitech quick cam. I checked the version of the cam and I found drivers that claim to work, but I can NOT compile them. I tried to look for post about this, but most of them were never came to a closure. here is what I did:
downloaded gspcav1-20071224 drivers
extracted them to /usr/src
cd /usr/src
make         ---> which gave errors

[CENTER]matthew@AMD-Turion117:/usr/src/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2604: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/usr/src/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:4407: fatal error: opening dependency file /usr/src/gspcav1-20071224/.gspca_core.o.d: Permission denied
compilation terminated.
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
[/CENTER]

What is wrong??

---

### Post by philinux on 2009-01-22
My logitech quick messenger works out the box. Did not have to install any drivers. I use kopete messenger.

---

### Post by bsharp on 2009-01-22
```
sudo make
```

Are you sure that you need to install drivers in the first place?

There might be an easier way.

---

### Post by annihilator89 on 2009-01-22
I tried using keopete and skype neither will work with the camera, I just see fuzzy green red white lines on a black background...
my camera is " ID 046d:092e Logitech, Inc. QuickCam Chat"

I did the "sudo make" I got this

matthew@AMD-Turion117:/usr/src/gspcav1-20071224$ sudo make
[sudo] password for matthew:
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2604: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
/usr/src/gspcav1-20071224/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2


----------

I also did "lsusb"

lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:092e Logitech, Inc. QuickCam Chat
Bus 001 Device 003: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I just tried the web cam with XAWTV and I can get a picture, it's not very good (it refreshes too obviously) but atleast I can see myself... I tried with keopete and skype, but no luck.
I don't know if it matters, but skype is looking for my camera at /dev/video0
I can't seem to figure out where xawTV is looking for it.

I just tried to restart with the camera plugged in and the XAwTV works great with the camera. Now how can I use the input it is getting and pass it to skype or keopete???

---

