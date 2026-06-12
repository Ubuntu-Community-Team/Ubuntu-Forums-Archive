---
title: "Please help with my webcam."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by TeresaStyles on 2009-01-27
I have an old Logitech Quickcam Express that I cannot figure out how to get to work. lsud reveals this:

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c041 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I go to test it out in Ekiga and get this:

Error while opening video device Logitech QuickCam USB

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

There was an error while opening the device. Please check your permissions and make sure that the appropriate driver is loaded

How to fix this?  Thanks much.

I forgot to add that I have 8.10.  I found the drivers at [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) but I assume I already have them since it recognized my camera.

---

### Post by TeresaStyles on 2009-01-27
This is not going to page two.

---

### Post by BDNiner on 2009-01-27
You will have to complie the drivers yourself inorder to get the camera to work. I quick search on google or this forum will show you numerous posts on getting this device working.

---

### Post by TeresaStyles on 2009-01-27
OK.  Thanks.  I was afraid of that (and afraid of compiling drivers).

---

### Post by TeresaStyles on 2009-01-27
This stinks.  After carefully following the instructions in the link in my first post it will not compile the driver:

make -C "/lib/modules/2.6.27-9-generic/build" SUBDIRS="/home/geof/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/geof/qc-usb-0.6.6/.tmp_versions ; rm -f /home/geof/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/geof/qc-usb-0.6.6
  gcc -Wp,-MD,/home/geof/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/geof/qc-usb-0.6.6/.tmp_qc-driver.o /home/geof/qc-usb-0.6.6/qc-driver.c
In file included from /home/geof/qc-usb-0.6.6/qc-driver.c:47:
/home/geof/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:16,
                 from /home/geof/qc-usb-0.6.6/quickcam.h:95,
                 from /home/geof/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/geof/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/geof/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/geof/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/geof/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/geof/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/geof/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/geof/qc-usb-0.6.6/qc-driver.c:2529: error: ‘struct video_device’ has no member named ‘type’
/home/geof/qc-usb-0.6.6/qc-driver.c: At top level:
/home/geof/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field ‘type’ specified in initializer
/home/geof/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/geof/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/geof/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [quickcam.ko] Error 2
geof@geof-desktop:~/qc-usb-0.6.6$

---

### Post by BentSlightly on 2009-01-28
Good Luck this is a huge problem that is not being addressed.

---

### Post by theDaveTheRave on 2009-02-21
Teresa

Sorry to have come upon this thread so late....

I'm going to assume you know absolutely nothing, so appologies if I insult your inteligence, but maybee this post will help other out also...

But, I must continue...

You obviously attempted to download and compile from source.

I'm not sure how you did this, but from looking at the thread that you posted it seemes not to have worked!

This is how I do it - but I'm sure there are other ways!

First I create a new directory called "downloads", then set firefox (or whatever web browser you like to use) to automatically save and downloaded files to this folder, otherwise you can end with a very messy desktop!

For setting up a web cam there is a nice little tool called EasyCam2, that will find and install the required modules. You can get it from [here]("https://help.ubuntu.com/community/EasyCam"), just click on the link and you will be taken to the page with the instructions for setting up EasyCam2.

For my system to work I needed to download a library file called libv4l-0.5.0, you can get it by clicking [here]("http://freshmeat.net/redir/libv4l/76006/url_tgz/libv4l-0.5.8.tar.gz")

So you've download your file.

Open a terminal, it should default to your "home" directory (you can often do <alt F2> or simlar to get a terminaly automatically. Otherwise you can find it in the menu under < Accessories | Terminal >

You should get a terminal window to open, with a propt that looks like this

```

geof@geof-desktop:~$

```

You will now need to change directory to your downloads directory

```

geof@geof-desktop:~$ cd downloads

```

for now we will pretend that you only have the easy cam download in your download directory, but you need to check by doing a listing, which should give you something like this

```

geof@geof-desktop:~/downloads$ls
libv4l-0.5.0.tar.gz

```

Now to unpack and run it etc do this command...

```

geof@geof-desktop:~/downloads$ tar -xvf libv4l-0.5.0.tar.gz
[sudo] password for  geof:

```

This has unpacked the file, you should see a few pages of "stuff" run through your screen, the switches '-xvf' have done the following
x - tells the tar command that you want to extract a tar archive
v - tells tar to be verbose - which is good, if it gets stuck somewhere it will send a message saying why.... hopefully.
f - tells tar that we are going to point it to a specified file.

so now we have unpacked our module, and it will have created another subdirectory that we need to go into with the following


```

geof@geof-desktop:~/downloads$ cd libv4l-0.5.0
geof@geof-desktop:~/downloads/libv4l-0.5.0$ 

```

which is what we want, this directory conatins all the files for loading the module, however it is a program, and it is in "source" code format, which means it is in fact simply a bunch of text files. So as it can run we need to 'make' it into a program that the computer can understand, to do this

```

geof@geof-desktop:~/downloads/libv4l-0.5.0$ make

```

again a load of info will pass through the screen.... now we need to 'instal' the programme into the computer so as it can run whenever the system needs it to. This is where things get "scary" you need to do this next part as "super user", however Ubuntu makes use of the <sudo> protocol (basically shorthand for "Super User DO ...."), you will then be asked to enter your password (if you aren't the administrator on your system then you'll need to get the person who is to do this part for you from their logon.

```

geof@geof-desktop:~/downloads/libv4l-0.5.0$ sudo make install
[sudo] password for  geof:

```

That should be job done... now you can follow the instructions in my first link for the installation of the EasyCam2, which is a much easier process.

Good Luck and I hope that explains a few things and helps you get stuff working.

David

---

