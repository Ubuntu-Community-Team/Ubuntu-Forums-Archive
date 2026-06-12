---
title: "Need your help; having big problems setting up Ndiswrapper."
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by Fabyfakid on 2007-11-29
I made a thread a couple of days ago about a problem I'm having with a "internet connection" button on my HP Pavilion laptop ([it's the [COLOR="Cyan"]"I"[/COLOR] button on this pic]("http://www.notebookreview.com/assets/7110.jpg")). It has a broadcom card, so I went and downloaded ndiswrapper in order to install the driver for it. I'm following the instruction on setting it up from the actual project, but I'm having a problem. Check out what I'm getting:

> fabian@fabian-laptop:~/Desktop/programs/ndiswrapper-1.50$ sudo make
Password:
make -C driver
make[1]: Entering directory `/home/fabian/Desktop/programs/ndiswrapper-1.50/driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/fabian/Desktop/programs/ndiswrapper-1.50/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

  Building modules, stage 2.
/usr/src/linux-headers-2.6.20-15-generic/scripts/Makefile.modpost:42: include/config/auto.conf: No such file or directory
make[3]: *** No rule to make target `include/config/auto.conf'.  Stop.
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/fabian/Desktop/programs/ndiswrapper-1.50/driver'
make: *** [all] Error 2
fabian@fabian-laptop:~/Desktop/programs/ndiswrapper-1.50$ cd /usr/src/linux-headers-2.6.20-15-generic
fabian@fabian-laptop:/usr/src/linux-headers-2.6.20-15-generic$ sudo make oldconfig && make prepare
scripts/kconfig/conf -o arch/i386/Kconfig
ubuntu/Kconfig:5: can't open file "ubuntu/misc/Kconfig"
make[1]: *** [oldconfig] Error 1
make: *** [oldconfig] Error 2
fabian@fabian-laptop:/usr/src/linux-headers-2.6.20-15-generic$ ls; cd ubuntu
arch   crypto   fs       init  kernel  Makefile  Module.symvers  scripts   sound   usr
block  drivers  include  ipc   lib     mm        net             security  ubuntu
fabian@fabian-laptop:/usr/src/linux-headers-2.6.20-15-generic/ubuntu$ ls
acpi  block  fs  include  Kconfig  mactel  Makefile  media  ms  net  ssb  wireless
fabian@fabian-laptop:/usr/src/linux-headers-2.6.20-15-generic/ubuntu$

As you see, there's no directory named "misc". However, I find strange that there's a directory named "block"; here's what's inside:

> fabian@fabian-laptop:/usr/src/linux-headers-2.6.20-15-generic/ubuntu$ cd block; ls
Kconfig  Makefile
fabian@fabian-laptop:/usr/src/linux-headers-2.6.20-15-generic/ubuntu/block$

Could it have something to do with the problem?

- I'm using Feisty, and version 1.50 of Ndiswrapper.

---

### Post by Fabyfakid on 2007-11-30
*bump* need your help guys

---

### Post by kevdog on 2007-11-30
Try doing this:

sudo aptitude install build-essential linux-headers-`uname -r`

Just copy and paste this into the command line.  This will install the build essential package (necessary to compile) and the linux headers needed to compile from source. (no rogue commands here!)

Then try to compile again

make distclean
make 
sudo make install

---

