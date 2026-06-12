---
title: "Internal dialup modem How to install driver"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by dineshs on 2009-03-10
I have an internal dialup modem .command lspci results ESS Technology ES2898 Modem (rev 03).Kindly guide me to install driver for this.I downloaded
[http://tx.technion.ac.il/~raindel/ess_2.6-v0.3.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.3.tar.gz).
but when tried to compile,gives an error

root@dinesh:/home/dinesh/ess_2.6-v0.3# ./setup
checking for running kernel version...2.6.27
checking for gcc...4.3.2
checking for kernel gcc version...4.3.2
searching for kernel includes...found at /lib/modules/2.6.27-7-generic/build/include
checking for autoconf.h.../lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in utsrelease.h...UTS_RELEASE is 2.6.27-7-generic
checking type of tty_struct.count...int
checking for presence of udev...present
detecting your modem...found. Your modem is a ess type modem.
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in make.log.  When reporting problems to
the development team, please send us this file.

---

### Post by Bearly Able on 2009-03-10
You may have been here already, but I found [this "How To"]("https://help.ubuntu.com/community/DialupModemHowto") very helpful; it includes a section on compiling from source, although I didn't need that part myself.

---

### Post by mikechant on 2009-03-10
> A transcript of the build process
has been saved in make.log.

Please post the contents of the make.log file.

---

### Post by dineshs on 2009-03-10
sorry for being late
LD	binary.a
make -C /lib/modules/2.6.27-7-generic/build M=/home/dinesh/ess_2.6-v0.3
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/dinesh/ess_2.6-v0.3/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/dinesh/ess_2.6-v0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2

---

### Post by mikechant on 2009-03-10
> scripts/Makefile.build:46: *** CFLAGS was changed in "/home/dinesh/ess_2.6-v0.3/Makefile". Fix it to use EXTRA_CFLAGS. Stop.

OK, this error seems to happen in a variety of cases when building drivers and there seem to be two solutions:
1/ Edit the makefile and change all occurrences of
CFLAGS to EXTRA_CFLAGS
2/ Changing the 'make' command (presumably in the 'setup' file) to 'make KBUILD_NOPEDANTIC=1 (plus whatever else was there before)'

For example, see this similar problem:
[http://hi.baidu.com/wzipp/blog/item/3b6d9f45799b5423cffca386.html](http://hi.baidu.com/wzipp/blog/item/3b6d9f45799b5423cffca386.html)

---

