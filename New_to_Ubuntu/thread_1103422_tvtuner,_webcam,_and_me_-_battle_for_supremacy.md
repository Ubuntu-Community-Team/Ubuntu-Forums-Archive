---
title: "tvtuner, webcam, and me - battle for supremacy"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by il-luzhin on 2009-03-22
Well after two days I'm going to quit reading and start posting.

I've gotten a Logitech QuickCam and though I've read there are issues with this model I'm having little success finding solutions to my particular issue.

When I attempt to select a video device my Hauppaugge WinTV PVR-150 tv tuner is always an option but my webcam is never an option.  The webcam does show up on lsusb so I'm somewhat lost.

---

### Post by il-luzhin on 2009-03-22
I'm failing to build modules properly.  My God, am I about to get a crash course in compiling?  BTW, I'm on a 64-bit system which may be a big part of my issues.  

```

luzhin@kerenin:~/gspcav1-20071224$ sudo ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/luzhin/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/luzhin/gspcav1-20071224/gspca_core.o
/home/luzhin/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/luzhin/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/luzhin/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/home/luzhin/gspcav1-20071224/gspca_core.c: At top level:
/home/luzhin/gspcav1-20071224/gspca_core.c:2607: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/luzhin/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initializer
/home/luzhin/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/luzhin/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initializer
/home/luzhin/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/luzhin/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/home/luzhin/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/home/luzhin/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/luzhin/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/home/luzhin/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/luzhin/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2


```

any advice is appreciated

---

