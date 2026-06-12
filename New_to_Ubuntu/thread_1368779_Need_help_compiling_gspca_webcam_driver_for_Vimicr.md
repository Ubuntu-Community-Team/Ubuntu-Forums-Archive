---
title: "Need help compiling gspca webcam driver for Vimicro"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by KcLKcL on 2009-12-31
**Here's what I did:**

```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz

wget http://www.bairesnortelug.com.ar/diff/gspca.diff

tar -zxvf gspcav1-20071224.tar.gz

cd gspcav1-20071224

cat ../gspca.diff | patch -p1
patching file gspca.h
patching file gspca_core.c
```Okay, seems fine, now I'm trying to compile & build this

```
arif@arif-desktop:~/gspcav1-20071224$ ./gspca_build

 FATAL !! you must be root to run this script
arif@arif-desktop:~/gspcav1-20071224$ sudo ./gspca_build
[sudo] password for arif: 

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
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/arif/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-020632-generic'
  CC [M]  /home/arif/gspcav1-20071224/gspca_core.o
In file included from /home/arif/gspcav1-20071224/gspca_core.c:845:
/home/arif/gspcav1-20071224/utils/spcausb.h: In function &#8216;spca5xxRegRead&#8217;:
/home/arif/gspcav1-20071224/utils/spcausb.h:95: error: implicit declaration of function &#8216;info&#8217;
/home/arif/gspcav1-20071224/utils/spcausb.h: In function &#8216;spca_set_interface&#8217;:
/home/arif/gspcav1-20071224/utils/spcausb.h:278: error: implicit declaration of function &#8216;warn&#8217;
In file included from /home/arif/gspcav1-20071224/gspca_core.c:853:
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function &#8216;sp5xxfw2_init&#8217;:
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:122: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:136: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:141: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:148: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:176: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function &#8216;sp5xxfw2_start&#8217;:
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:214: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:230: error: called object &#8216;info&#8217; is not a function
/home/arif/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/home/arif/gspcav1-20071224/gspca_core.c:2463: warning: passing argument 1 of &#8216;video_usercopy&#8217; from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected &#8216;struct file *&#8217; but argument is of type &#8216;struct inode *&#8217;
/home/arif/gspcav1-20071224/gspca_core.c:2463: warning: passing argument 2 of &#8216;video_usercopy&#8217; makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected &#8216;unsigned int&#8217; but argument is of type &#8216;struct file *&#8217;
/home/arif/gspcav1-20071224/gspca_core.c:2463: warning: passing argument 4 of &#8216;video_usercopy&#8217; makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected &#8216;v4l2_kioctl&#8217; but argument is of type &#8216;long unsigned int&#8217;
/home/arif/gspcav1-20071224/gspca_core.c:2463: error: too many arguments to function &#8216;video_usercopy&#8217;
/home/arif/gspcav1-20071224/gspca_core.c: At top level:
/home/arif/gspcav1-20071224/gspca_core.c:2615: warning: initialization from incompatible pointer type
make[2]: *** [/home/arif/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/arif/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-020632-generic'
make: *** [default] Error 2

```Any ideas? Need Help..
I've been searching around Google, and got no solution at all...
--------------------
[B][I]EDIT: Apparently It's like something related to gspca eh? I don't know how to fix this..
[/I][/B][I]LOAD gspca in memory 
FATAL: Module gspca not found.[/I]****

---

### Post by blazemore on 2010-01-09
What happens if you
```
sudo modprobe gspca
```

---

### Post by oe3cjb on 2010-01-15
HI,

I've the same problem. I am also not able to compile.
It seems to be some problem with these lines

In file included from /home/arif/gspcav1-20071224/gspca_core.c:845:
/home/arif/gspcav1-20071224/utils/spcausb.h: In function &#8216;spca5xxRegRead&#8217;:
/home/arif/gspcav1-20071224/utils/spcausb.h:95: error: implicit declaration of function &#8216;info&#8217;
/home/arif/gspcav1-20071224/utils/spcausb.h: In function &#8216;spca_set_interface&#8217;:
/home/arif/gspcav1-20071224/utils/spcausb.h:278: error: implicit declaration of function &#8216;warn&#8217;
In file included from /home/arif/gspcav1-20071224/gspca_core.c:853:
/home/arif/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function &#8216;sp5xxfw2_init&#8217;:

It looks like, one header-file is missing or so, because 'info' and 'warn' are missing.

Any idea?

Regards
Christian

---

### Post by KcLKcL on 2010-01-16
> **blazemore said:**
> What happens if you
```
sudo modprobe gspca
```

Sorry for the late reply but...
This is what I got:

```
arif@arif-desktop:~$ sudo modprobe gspca
[sudo] password for arif: 
FATAL: Module gspca not found.
```

My gspca is broken? I guess?

---

### Post by no2498 on 2010-01-16
try this open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2

cam should come on

get a program like (cheese) or (wxcam)
see if they find the cam

---

### Post by KcLKcL on 2010-01-17
> **no2498 said:**
> try this open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2

cam should come on

get a program like (cheese) or (wxcam)
see if they find the cam

WOW IT WORKS NOW! Thanks alot!

Cheers!

Apparently I don't have to compile the driver again on 9.10 :D

---

### Post by El_Perro_Perduto on 2010-02-05
Still having trouble configuring my Logitech QuickCam for Notebooks with 9.10.  I can send and receive audio on skype but I can only receive video.
The skype video settings seem to recognize the camera (skype calls it USB Camera (046d:08dd) (/dev/video0). When I hit the test button, nothing happens -- I double click it and get a blank grey screen.  

Tried configuring the video with gstreamer-properties.  This worked, I'm using the v4l2 plugin and it seems to recognize the camera. In gstreamer the testing works, I see video.  Why doesn't this work with skype?

please help

---

### Post by ProNux on 2010-05-30
> **no2498 said:**
> try this open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2

cam should come on

get a program like (cheese) or (wxcam)
see if they find the cam
hello,

I have a similar scenario and I got errors after testing the v4l1 and v4l2.
"Video for Linux (v4l): Device "/dev/video0" does not exist"
"Video for Linux 2 (v4l2): Cannot identify device '/dev/video0"

I really wanted to make my webcam work on my Asus A8J after deciding to switch to Linux.  I am still searching for any solution.  Thanks in advance.

---

### Post by ProNux on 2010-05-30
> **KcLKcL said:**
> WOW IT WORKS NOW! Thanks alot!

Cheers!

Apparently I don't have to compile the driver again on 9.10 :D

Hello,

Do you have other steps aside from the "gstreamer-properties"? I follow the same procedure but I can't get it working.

---

### Post by ProNux on 2010-05-30
here's  my output after the "build" command.
```
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
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/polymath/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/polymath/gspcav1-20071224/gspca_core.o
/home/polymath/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /home/polymath/gspcav1-20071224/gspca_core.c:845:
/home/polymath/gspcav1-20071224/utils/spcausb.h: In function ‘spca5xxRegRead’:
/home/polymath/gspcav1-20071224/utils/spcausb.h:95: error: implicit declaration of function ‘info’
/home/polymath/gspcav1-20071224/utils/spcausb.h: In function ‘spca_set_interface’:
/home/polymath/gspcav1-20071224/utils/spcausb.h:278: error: implicit declaration of function ‘warn’
In file included from /home/polymath/gspcav1-20071224/gspca_core.c:853:
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_init’:
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:122: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:136: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:141: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:148: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:176: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_start’:
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:214: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:230: error: called object ‘info’ is not a function
/home/polymath/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/polymath/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/polymath/gspcav1-20071224/gspca_core.c: At top level:
/home/polymath/gspcav1-20071224/gspca_core.c:2604: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/polymath/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/polymath/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/polymath/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/polymath/gspcav1-20071224/gspca_core.c:2615: warning: initialization from incompatible pointer type
/home/polymath/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/polymath/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/polymath/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/polymath/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/polymath/gspcav1-20071224/gspca_core.c:4301: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
make[2]: *** [/home/polymath/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/polymath/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [default] Error 2
```
I don't know these errors.  My camera is 
```
Bus 001 Device 003: ID 0ac8:0321 Z-Star Microelectronics Corp. Vimicro generic vc0321 Camera

```
Any help please...

---

### Post by ProNux on 2010-05-30
After a restart, I got the camera working.  But I noticed the image quality is poor.  Is this really normal?  Any users having the same camera (0ac8x0321)? Thanks.

---

### Post by no2498 on 2010-06-02
see you digging up old threads

most webcams do not need drivers now days

910 and up cheese webcam booth is/should be installed
look in sound & video

try the cam in cheese

---

### Post by frisket on 2010-06-07
> **KcLKcL said:**
> **Here's what I did:**

```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz

wget http://www.bairesnortelug.com.ar/diff/gspca.diff

tar -zxvf gspcav1-20071224.tar.gz

cd gspcav1-20071224

cat ../gspca.diff | patch -p1
patching file gspca.h
patching file gspca_core.c
```

I had hoped the patch would address the compiletime errors but it doesn't. gspca is fatally broken for Karmic and there are no signs that it is going to be fixed.

---

### Post by 3esmit on 2010-06-07
now gspca comes with kernel

_lsmod | grep zc3xx_
*Module                      Size         Used by*
gspca_zc3xx         49253  0 
gspca_main           25031  1     gspca_zc3xx

---

### Post by ProNux on 2010-06-11
> **no2498 said:**
> see you digging up old threads

most webcams do not need drivers now days

910 and up cheese webcam booth is/should be installed
look in sound & video

try the cam in cheese

Thanks.  The cam works now, even in virtualbox. My problem is the detection is intermittent using ```
gstreamer-properties
```.  Sometimes, I need to reboot and try my luck on the next boot.  Success rate is around 60%.  (6/10 boots detects my webcam).

---

### Post by afrodeity on 2010-09-05
checked out the gspca code from bzr

bzr branch lp:ubuntu/lucid/gspca

```

sudo ./gspca_build

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
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/modules/gspca_core.o
/usr/src/modules/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /usr/src/modules/gspca_core.c:845:
/usr/src/modules/utils/spcausb.h: In function ‘spca5xxRegRead’:
/usr/src/modules/utils/spcausb.h:95: error: implicit declaration of function ‘info’
/usr/src/modules/utils/spcausb.h: In function ‘spca_set_interface’:
/usr/src/modules/utils/spcausb.h:278: error: implicit declaration of function ‘warn’
In file included from /usr/src/modules/gspca_core.c:853:
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_init’:
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:122: error: called object ‘info’ is not a function
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:136: error: called object ‘info’ is not a function
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:141: error: called object ‘info’ is not a function
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:148: error: called object ‘info’ is not a function
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:176: error: called object ‘info’ is not a function
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_start’:
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:214: error: called object ‘info’ is not a function
/usr/src/modules/Sunplus-jpeg/sp5xxfw2.h:230: error: called object ‘info’ is not a function
/usr/src/modules/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/modules/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/gspca_core.c: At top level:
/usr/src/modules/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/modules/gspca_core.c:2615: warning: initialization from incompatible pointer type
/usr/src/modules/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/modules/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/modules/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/modules/gspca_core.c:4301: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
make[2]: *** [/usr/src/modules/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [default] Error 2

```

problems building on lucid

---

