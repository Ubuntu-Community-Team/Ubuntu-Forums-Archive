---
title: "how to install a driver"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Ewan Cameron on 2009-10-25
i am trying to get my sony vaio vgn-tz37 gn to fully work with ubuntu.

I am working on the webcam.

I have downloaded a driver which looks promising. It downloaded as a file with ending in .tar.bz2. I have unpacked this to a folder called /home/ken/Desktop/r5u870-VCC6 which contans a large  number of files.
[IMG]file:///home/ken/Desktop/Screenshot.png[/IMG]
[IMG]file:///home/ken/Desktop/Screenshot.png[/IMG]I have attached a screenshot of the contents of this folder.

I have looked in the readme file in this folder but have been unable to use it to install the driver.

The readme file contains the following about installing and loading:

[INDENT]I[I]nstallation Process
====================

To attempt to build against the running kernel:

make

To build against a specific kernel:

make KDIR=/path/to/kernel

To install the modules to the appropriate location:

make install

-or-

make install KDIR=/path/to/kernel

Installed modules will be automatically probed for supported devices by the
udev coldplug component at boot, and the driver should be automatically
loaded on subsequent reboots.

NOTE: Previous releases of this driver have produced modules named
ry5u870.ko.  With the current release, the module name was changed to
r5u870.ko.  Ensure that any old versions are deleted after installing a
new version.


Loading the Driver
==================

If you installed the driver, you can just run:

modprobe r5u870

If you wish to load the driver without installing it, you must load the
prerequisite modules:

modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32        (on 64-bit platforms)

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:

insmod r5u870.ko[/I]
[/INDENT]

I simply can't make sense of any of this.Can anyone point me in a useful direction /

kc

---

### Post by sandyd on 2009-10-25
> **Ewan Cameron said:**
> i am trying to get my sony vaio vgn-tz37 gn to fully work with ubuntu.

I am working on the webcam.

I have downloaded a driver which looks promising. It downloaded as a file with ending in .tar.bz2. I have unpacked this to a folder called /home/ken/Desktop/r5u870-VCC6 which contans a large  number of files.
[IMG]file:///home/ken/Desktop/Screenshot.png[/IMG]
[IMG]file:///home/ken/Desktop/Screenshot.png[/IMG]I have attached a screenshot of the contents of this folder.

I have looked in the readme file in this folder but have been unable to use it to install the driver.

The readme file contains the following about installing and loading:
[INDENT]I[I]nstallation Process
====================

To attempt to build against the running kernel:

make

To build against a specific kernel:

make KDIR=/path/to/kernel

To install the modules to the appropriate location:

make install

-or-

make install KDIR=/path/to/kernel

Installed modules will be automatically probed for supported devices by the
udev coldplug component at boot, and the driver should be automatically
loaded on subsequent reboots.

NOTE: Previous releases of this driver have produced modules named
ry5u870.ko.  With the current release, the module name was changed to
r5u870.ko.  Ensure that any old versions are deleted after installing a
new version.


Loading the Driver
==================

If you installed the driver, you can just run:

modprobe r5u870

If you wish to load the driver without installing it, you must load the
prerequisite modules:

modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32        (on 64-bit platforms)

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:

insmod r5u870.ko[/I]
[/INDENT]I simply can't make sense of any of this.Can anyone point me in a useful direction /

kc
using the terminal, cd into the directory.
then
```

make
sudo make install
[I]sudo cp r5u870_*.fw /lib/firmware
[/I]*modprobe r5u870*
[I]
```

then
```

sudo gedit /etc/modules

```
insert this on a new blank line on the bottom of the file and hit save.

```

r5u970
```
[/I]

---

### Post by Ewan Cameron on 2009-10-25
thanks dolphinaura. i tried as advised, and got the following:

ken@ken-laptop:~/Desktop/r5u870-VCC6$ make
make -C /lib/modules/2.6.28-15-generic/build M=/home/ken/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/ken/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/ken/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/ken/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ken/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ken/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
ken@ken-laptop:~/Desktop/r5u870-VCC6$ make install
make -C /lib/modules/2.6.28-15-generic/build M=/home/ken/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/ken/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/ken/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/ken/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ken/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ken/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
ken@ken-laptop:~/Desktop/r5u870-VCC6$ sudo cp r5u870_*/lib/firmware
[sudo] password for ken: 
cp: missing destination file operand after `r5u870_*/lib/firmware'
Try `cp --help' for more information.
ken@ken-laptop:~/Desktop/r5u870-VCC6$ sudo cp r5u870_*.fw /lib/firmware
ken@ken-laptop:~/Desktop/r5u870-VCC6$ modprobe r5u870
FATAL: Module r5u870 not found.

probably should not have blundered on after the first lot of errors...

---

### Post by sandyd on 2009-10-25
> **Ewan Cameron said:**
> thanks dolphinaura. i tried as advised, and got the following:

ken@ken-laptop:~/Desktop/r5u870-VCC6$ make
make -C /lib/modules/2.6.28-15-generic/build M=/home/ken/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/ken/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/ken/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/ken/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ken/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ken/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
ken@ken-laptop:~/Desktop/r5u870-VCC6$ make install
make -C /lib/modules/2.6.28-15-generic/build M=/home/ken/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/ken/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/ken/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/ken/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ken/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ken/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
ken@ken-laptop:~/Desktop/r5u870-VCC6$ sudo cp r5u870_*/lib/firmware
[sudo] password for ken: 
cp: missing destination file operand after `r5u870_*/lib/firmware'
Try `cp --help' for more information.
ken@ken-laptop:~/Desktop/r5u870-VCC6$ sudo cp r5u870_*.fw /lib/firmware
ken@ken-laptop:~/Desktop/r5u870-VCC6$ modprobe r5u870
FATAL: Module r5u870 not found.

probably should not have blundered on after the first lot of errors...
yow. big mistake on my part.

forgot to add
```

sudo apt-get install linux-headers-generic linux-source

```

---

