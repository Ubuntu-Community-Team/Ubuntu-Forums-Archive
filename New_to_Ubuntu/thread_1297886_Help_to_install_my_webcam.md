---
title: "Help to install my webcam ?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by kkram on 2009-10-22
[FONT=Arial Black]hi to u all !
my problem is with my logitech quickcam express m/n: v-uh9

[IMG]http://hitech-online.ru/bank/articles/quickcam_express_v_uh9.jpg[/IMG]

i can't make it work...in ubuntu 9.04......
my lsusb is.. bus 003 device 002: 046d:0870 logitech, inc. QuickCam Express...
my kernel is... linux 2.6.28-16-generic.....gnome 2.26.1
i used the qc-usb 0.6.6.tar.gz but nothing

[/FONT]```
ratk@ratk-desktop:~$ cd /home/ratk/qc-usb-0.6.6
ratk@ratk-desktop:~/qc-usb-0.6.6$ make
-=- Logitech QuickCam USB camera driver -=-

Makefile target examples:
make all - Compile driver and utilities against current running kernel
make all USER_OPT=-DDEBUG - Compile with debugging code and messages
make all LINUX_DIR=/usr/src/linux - Compile against specified kernel source
make install - Copy driver and utilities into standard locations (needs root)
make install PREFIX=/usr - Copy utilities to /usr/bin instead of /usr/local/bin
make install MODULE_DIR=/lib/modules/2.4.0 - Copy module to /lib/modules/2.4.0/misc
make clean - Remove object files from the source directory

Current configuration:
Driver source directory (PWD):         /home/ratk/qc-usb-0.6.6
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.28-16-generic/build
Module install directory (MODULE_DIR): /lib/modules/2.6.28-16-generic
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):               -DHAVE_UTSRELEASE_H=1
Driver file name (use with insmod):    quickcam.ko    
Kernel version code:                   132636

ratk@ratk-desktop:~/qc-usb-0.6.6$ make install
make -C "/lib/modules/2.6.28-16-generic/build" SUBDIRS="/home/ratk/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/ratk/qc-usb-0.6.6/.tmp_versions ; rm -f /home/ratk/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/ratk/qc-usb-0.6.6
  gcc -Wp,-MD,/home/ratk/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-16-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)"  -c -o /home/ratk/qc-usb-0.6.6/.tmp_qc-driver.o /home/ratk/qc-usb-0.6.6/qc-driver.c
In file included from /home/ratk/qc-usb-0.6.6/qc-driver.c:47:
/home/ratk/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:16,
                 from /home/ratk/qc-usb-0.6.6/quickcam.h:95,
                 from /home/ratk/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_i2c_init&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:824: error: &#8216;struct urb&#8217; has no member named &#8216;lock&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_isoc_start&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_v4l_poll&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:2256: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_v4l_open&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:2308: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_v4l_close&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:2376: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_v4l_read&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:2424: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_v4l_mmap&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:2479: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_v4l_ioctl&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:2511: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c:2529: error: &#8216;struct video_device&#8217; has no member named &#8216;type&#8217;
/home/ratk/qc-usb-0.6.6/qc-driver.c: At top level:
/home/ratk/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field &#8216;type&#8217; specified in initializer
/home/ratk/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field &#8216;hardware&#8217; specified in initializer
/home/ratk/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_usb_init&#8217;:
/home/ratk/qc-usb-0.6.6/qc-driver.c:3158: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
make[2]: *** [/home/ratk/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/ratk/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-generic'
make: *** [quickcam.ko] Error 2
ratk@ratk-desktop:~/qc-usb-0.6.6$ 

```................[FONT=Arial Black]what can i do ???[/FONT]

---

### Post by kkram on 2009-10-23
i know that compiling isn't the smartest .....but what can i do ??](*,)

---

### Post by Chronon on 2009-10-23
Maybe try:
"make all", then "make install".

---

### Post by MelDJ on 2009-10-23
try [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by 3rdalbum on 2009-10-23
Have you got the linux-headers-generic package installed? You need the kernel headers in order to compile a kernel module.

Ubuntu will not actually do anything visible when you plug in the webcam - so you're definitely sure it doesn't work in, say, Cheese?

---

### Post by rileyrg on 2009-11-11
> **MelDJ said:**
> try [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")

I am intrigued to know how your reply is any way pertinent to the issues the OP is having? Did you even read his issue? FWIW, I am having the exact same issue.

---

### Post by rileyrg on 2009-11-11
> **3rdalbum said:**
> Have you got the linux-headers-generic package installed? You need the kernel headers in order to compile a kernel module.

Ubuntu will not actually do anything visible when you plug in the webcam - so you're definitely sure it doesn't work in, say, Cheese?

The error reports are because of mismatched structures. Not missing headers.

---

### Post by rileyrg on 2009-11-11
> **Chronon said:**
> Maybe try:
"make all", then "make install".

Same errors when using "m-a a-i qc-usb".

Making wild guesses helps no one.

---

### Post by JohnnyJonJon on 2009-11-17
Ok so the problem comes from the new 2.6.30 kernel, the structs were removed and altered, so the source code needs to be changed, qc-cam source that is.  I emailed the dev a few days ago but have received no responce(you can [EMAIL="mag@mag.cx"]mag@mag.cx[/EMAIL]).

I commented out the lines which refer to struct proc_dir_entry owner, no problem there.

Now I am struct at the ‘struct video_device’...  The error happens at the instantiation of a custom qc struct .  look like everything depends on this struct and not a simple comment out fix, i expect doing that would create massive amounts of compile errors.

Someone with a lot more code knowledge will need to fix this.

---

### Post by no2498 on 2009-11-18
have you pluged the cam in then restarted the computer
an do you have the programs like cheese or wxcam
an try typeing ( gstreamer-properties ) in the terminal
click video try diff settings

---

### Post by cariboo on 2009-11-18
Could you open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n15
```

and paste the output in your next post. 

I was given [this]("http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/5868&cl=us,en") webcam about a year ago, It wouldn't work running Intrepid, but last night I plugged it in my laptop running Karmic and it was detected and the driver was loaded. I installed cheese and got a picture when I opened the program.

---

### Post by gradinaruvasile on 2009-11-18
No need to install anything to see if the webcam is working out of the box. see here:

[http://ubuntuforums.org/showthread.php?t=1330272](http://ubuntuforums.org/showthread.php?t=1330272)

If that doesnt work, you need to install drivers...

---

