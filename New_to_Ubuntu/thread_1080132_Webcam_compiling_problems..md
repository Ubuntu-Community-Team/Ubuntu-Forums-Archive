---
title: "Webcam compiling problems."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by dlawler on 2009-02-25
when trying to compile my driver for my webcam, i follow this guide.
1. install what's needed:
 $ sudo apt-get install mercurial build-essential libusb-dev libglib2.0-dev

2. Fetch source:
 $ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)

3. Change into r5u87x directory
 $ cd r5u87x

4. Compile
 $ make

5. It's very short and then you'll need to load driver so do this next
 $ sudo ./loader

well, it's all fine and dandy, until i get to make.

this is what happens:

daniel@daniel-laptop:~/r5u87x$ make
make: Nothing to be done for `all'.
daniel@daniel-laptop:~/r5u87x$ 

please help.
i need it for my online college courses. :( 
haha.

---

### Post by yoyoned on 2009-02-26
please post more of the output of make

---

### Post by dlawler on 2009-02-27
that is the complete output of make.

---

### Post by taurus on 2009-02-27
While you are in that directory, ~/r5u87x, post the output of this command.

```
ls -la
```

---

### Post by dlawler on 2009-02-28
daniel@daniel-laptop:~/r5u87x$ ls -la
total 7392
drwxr-xr-x 14 daniel daniel    4096 2009-02-25 04:00 .
drwxr-xr-x 96 daniel daniel    4096 2009-02-27 07:59 ..
-rw-r--r--  1 daniel daniel    2661 2005-02-13 13:05 acinclude.m4
-rw-r--r--  1 daniel daniel  244051 2006-03-03 21:53 aclocal.m4
drwxrwxrwx  2 daniel daniel    4096 2006-03-03 22:01 apidocs
-rw-r--r--  1 daniel daniel     130 2004-04-21 19:00 AUTHORS
-rw-r--r--  1 daniel daniel   16833 2006-03-03 21:52 bsd.c
-rw-r--r--  1 daniel daniel       0 2008-01-25 08:28 build-stamp
-rw-r--r--  1 daniel daniel    7358 2008-01-25 07:44 ChangeLog
-rwxr-xr-x  1 daniel daniel    3642 2004-03-12 02:18 compile
-rwxr-xr-x  1 daniel daniel   42037 2004-04-11 22:01 config.guess
-rw-r--r--  1 daniel daniel     268 2009-02-19 10:12 config.h
-rw-r--r--  1 daniel daniel    2467 2006-03-03 21:56 config.h.in
-rw-r--r--  1 daniel daniel   42095 2009-02-25 03:45 config.log
-rwxr-xr-x  1 daniel daniel   40430 2009-02-25 03:45 config.status
-rwxr-xr-x  1 daniel daniel   30221 2004-04-11 22:01 config.sub
-rwxr-xr-x  1 daniel daniel  746195 2006-03-03 21:54 configure
-rw-r--r--  1 daniel daniel    6777 2006-03-03 21:53 configure.in
-rw-r--r--  1 daniel daniel       0 2008-01-25 08:28 configure-stamp
drwxr-xr-x  2 daniel daniel    4096 2009-02-25 04:00 contrib
-rw-r--r--  1 daniel daniel   18011 2008-01-25 07:44 COPYING
-rw-r--r--  1 daniel daniel   35685 2006-03-03 21:52 darwin.c
drwxr-xr-x  3 daniel daniel    4096 2008-02-10 12:44 debian
-rwxr-xr-x  1 daniel daniel   14841 2004-03-12 02:18 depcomp
drwxr-xr-x  2 daniel daniel    4096 2009-02-25 03:46 .deps
-rw-r--r--  1 daniel daniel   15021 2006-03-03 21:52 descriptors.c
-rw-r--r--  1 daniel daniel     322 2009-02-25 03:45 descriptors.lo
-rw-r--r--  1 daniel daniel   32880 2009-02-25 03:45 descriptors.o
drwxrwxrwx  2 daniel daniel    4096 2009-02-25 03:45 doc
drwxr-xr-x  2 daniel daniel    4096 2009-02-25 04:00 docs
-rw-r--r--  1 root   root     44099 2009-02-25 03:45 Doxyfile
-rw-r--r--  1 daniel daniel   44154 2006-02-06 18:46 Doxyfile.in
-rw-r--r--  1 daniel daniel     759 2004-01-27 17:36 error.c
-rw-r--r--  1 daniel daniel     716 2004-01-27 17:36 error.h
-rw-r--r--  1 daniel daniel     304 2009-02-25 03:45 error.lo
-rw-r--r--  1 daniel daniel    5776 2009-02-25 03:45 error.o
drwxr-xr-x  3 daniel daniel    4096 2009-02-15 18:48 .hg
-rw-r--r--  1 daniel daniel      94 2009-02-19 10:12 .hg_archival.txt
-rw-r--r--  1 root   root      2043 2009-02-25 03:45 INSTALL.libusb
-rw-r--r--  1 daniel daniel    2063 2004-01-27 17:36 INSTALL.libusb.in
-rwxr-xr-x  1 daniel daniel    9208 2004-03-12 02:18 install-sh
-rw-r--r--  1 daniel daniel      26 2008-01-25 07:44 Kbuild
drwxr-xr-x  2 daniel daniel    4096 2009-02-25 03:46 .libs
-rwxr-xr-x  1 root   root    203453 2009-02-25 03:45 libtool
drwxrwxrwx  2 daniel daniel    4096 2009-02-19 06:49 libusb-0.1.12
-rwxr-xr-x  1 root   root      1267 2009-02-25 03:45 libusb-config
-rw-r--r--  1 daniel daniel    1267 2004-01-27 17:36 libusb-config.in
-rw-r--r--  1 daniel daniel     794 2009-02-25 03:46 libusb.la
-rw-r--r--  1 root   root       206 2009-02-25 03:45 libusb.pc
-rw-r--r--  1 daniel daniel     196 2005-02-14 15:46 libusb.pc.in
-rw-r--r--  1 daniel daniel    1047 2009-02-25 03:46 libusbpp.la
-rw-r--r--  1 root   root      1290 2009-02-25 03:45 libusb.spec
-rw-r--r--  1 daniel daniel    1293 2006-03-03 21:52 libusb.spec.in
-rw-r--r--  1 daniel daniel    2248 2004-01-27 17:36 LICENSE
-rw-r--r--  1 daniel daniel   19148 2006-03-03 21:52 linux.c
-rw-r--r--  1 daniel daniel    3146 2005-02-02 17:00 linux.h
-rw-r--r--  1 daniel daniel     304 2009-02-25 03:46 linux.lo
-rw-r--r--  1 daniel daniel   59776 2009-02-25 03:46 linux.o
-rwxr-xr-x  1 daniel daniel   28402 2009-02-20 20:25 loader
-rw-r--r--  1 daniel daniel   13799 2009-02-19 10:12 loader.c
-rw-r--r--  1 daniel daniel    2443 2009-02-19 10:12 loader.h
-rw-r--r--  1 daniel daniel 4475600 2009-02-20 20:25 loader.h.gch
-rw-r--r--  1 daniel daniel   27456 2009-02-20 20:25 loader.o
-rw-r--r--  1 daniel daniel  183730 2004-04-11 22:01 ltmain.sh
-rw-r--r--  1 daniel daniel    2390 2009-02-19 10:12 Makefile
-rw-r--r--  1 daniel daniel    2220 2006-03-03 21:52 Makefile.am
-rw-r--r--  1 daniel daniel   34139 2006-03-03 21:54 Makefile.in
-rwxr-xr-x  1 daniel daniel   10678 2004-03-12 02:18 missing
-rw-r--r--  1 daniel daniel      87 2008-06-02 17:00 modules.order
-rw-r--r--  1 daniel daniel    2750 2008-06-02 16:59 Module.symvers
-rw-r--r--  1 daniel daniel       8 2004-01-27 17:36 NEWS
-rw-r--r--  1 daniel daniel   16248 2008-01-25 07:44 r5u870_1810.fw
-rw-r--r--  1 daniel daniel   15794 2008-01-25 07:44 r5u870_1812.fw
-rw-r--r--  1 daniel daniel   15380 2008-01-25 07:44 r5u870_1830.fw
-rw-r--r--  1 daniel daniel   16224 2008-01-25 07:44 r5u870_1832.fw
-rw-r--r--  1 daniel daniel   12787 2008-01-25 07:44 r5u870_1833.fw
-rw-r--r--  1 daniel daniel   11834 2008-01-25 07:44 r5u870_1834.fw
-rw-r--r--  1 daniel daniel   16330 2008-01-25 07:44 r5u870_1835.fw
-rw-r--r--  1 daniel daniel   15537 2008-01-25 07:44 r5u870_1836.fw
-rw-r--r--  1 daniel daniel   14876 2008-01-25 07:44 r5u870_1839.fw
-rw-r--r--  1 daniel daniel   16729 2008-01-25 07:44 r5u870_183a.fw
-rw-r--r--  1 daniel daniel   16285 2008-01-25 08:28 r5u870_183b.fw
-rw-r--r--  1 daniel daniel   13357 2008-01-25 07:44 r5u870_1870_1.fw
-rw-r--r--  1 daniel daniel   13722 2008-01-25 07:44 r5u870_1870.fw
-rw-r--r--  1 daniel daniel   76908 2008-01-25 07:44 r5u870.c
-rw-r--r--  1 daniel daniel   34115 2008-06-02 16:59 r5u870.ko
-rw-r--r--  1 daniel daniel    1180 2008-06-02 16:59 r5u870.mod.c
-rw-r--r--  1 daniel daniel    6620 2008-06-02 16:59 r5u870.mod.o
-rw-r--r--  1 daniel daniel   28068 2008-06-02 16:52 r5u870.o
-rw-r--r--  1 daniel daniel    4032 2009-02-19 10:12 README
-rw-r--r--  1 daniel daniel    6633 2008-01-25 07:44 README.htm
-rw-r--r--  1 daniel daniel    2556 2006-03-03 21:52 README.in
-rwxr-xr-x  1 daniel daniel    3074 2009-02-19 10:12 recode-fw.scm
-rw-r--r--  1 daniel daniel      23 2009-02-25 03:45 stamp-h1
drwxrwxrwx  4 daniel daniel    4096 2009-02-25 03:46 tests
drwxr-xr-x  2 daniel daniel    4096 2009-02-25 04:00 ucode
-rw-r--r--  1 daniel daniel    6443 2006-03-03 21:52 usb.c
drwxr-xr-x  2 daniel daniel    4096 2008-06-02 17:00 usbcam
-rw-r--r--  1 root   root      8347 2009-02-25 03:45 usb.h
-rw-r--r--  1 daniel daniel    8367 2006-03-03 21:52 usb.h.in
-rw-r--r--  1 daniel daniel    1771 2006-03-03 21:52 usbi.h
-rw-r--r--  1 daniel daniel     298 2009-02-25 03:45 usb.lo
-rw-r--r--  1 daniel daniel   25328 2009-02-25 03:45 usb.o
-rw-r--r--  1 daniel daniel   13511 2006-03-03 21:52 usbpp.cpp
-rw-r--r--  1 daniel daniel   24428 2005-02-09 17:39 usbpp.h
-rw-r--r--  1 daniel daniel     304 2009-02-25 03:46 usbpp.lo
-rw-r--r--  1 daniel daniel  332976 2009-02-25 03:46 usbpp.o

---

### Post by taurus on 2009-02-28
You got all those files from unpacking r5u87x-50058c4bc1cd.tar.bz2!

Since there is a configure, try running that first.

```
./configure
```

---

### Post by dlawler on 2009-02-28
after a flavorful ./configure full of words and fragmented stuff the rest goes like this:

creating driver_name
make[2]: Leaving directory `/home/daniel/r5u87x/tests'
Making all in doc
make[2]: Entering directory `/home/daniel/r5u87x/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/daniel/r5u87x/doc'
make[1]: Leaving directory `/home/daniel/r5u87x'
daniel@daniel-laptop:~/r5u87x$ sudo ./loader
[sudo] password for daniel: 
r5u87x firmware loader v0.2

Searching for device...
Found camera: 0000:0000

Error: Failed to open /usr/lib/r5u87x/ucode/r5u87x-0000-0000.fw. Does it exist?
daniel@daniel-laptop:~/r5u87x$ 

... is it always one problem after the other? haha

---

### Post by dlawler on 2009-02-28
just so you know
here's the ls of .../ucode/

daniel@daniel-laptop:~/r5u87x$ cd ucode
daniel@daniel-laptop:~/r5u87x/ucode$ ls
r5u87x-05ca-1803.fw  r5u87x-05ca-1834.fw  r5u87x-05ca-183b.fw
r5u87x-05ca-1810.fw  r5u87x-05ca-1835.fw  r5u87x-05ca-183e.fw
r5u87x-05ca-1812.fw  r5u87x-05ca-1836.fw  r5u87x-05ca-1841.fw
r5u87x-05ca-1830.fw  r5u87x-05ca-1837.fw  r5u87x-05ca-1870_1.fw
r5u87x-05ca-1832.fw  r5u87x-05ca-1839.fw  r5u87x-05ca-1870.fw
r5u87x-05ca-1833.fw  r5u87x-05ca-183a.fw
daniel@daniel-laptop:~/r5u87x/ucode$ 

the 0000-0000.fw file obviously isn't there.
but i feel like that's a generic listing of a file that should exist in a chain...


or does it exist?

---

### Post by dlawler on 2009-03-02
is this thread officially abandoned?

---

