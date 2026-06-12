---
title: "Broadcom BCM4306 not recognized"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by pstoddard61 on 2005-12-01
Hi folks

This is my first experience with debian and ubuntu, and I'm not sure whether I am in the correct forum, but here goes.

I just installed ubuntu 2.6.12-9powerpc on my Mac 12" G4 Powerbook.  In addition to the basic desktop install, I installed 

gcc
gcc-3 base
gcc 4.0
gcc 4.0 base

My airport extreme card is not recognized.  It is a Broadcom BCM4306 802.11b/g wireless lan controller (rev 03), and apparently it is known not to be supported out of the box.  I think I need ndiswrapper.

I am reading the SetupNdiswrapperHowto, which describes ndiswrapper-1.1, but when I went to the download page I was handed the most recent one, ndiswrapper-1.6.  Shouldn't be a problem.   I expanded the .gz file to /usr/src and consulted the file /usr/src/ndiswrapper-1.6/INSTALL.  I tried a make, but it halts because it is looking for ggc-3.4.  Here is the error:

************snip***************

peter@ubuntu:/usr/src/ndiswrapper-1.6$ make
make -C driver
make[1]: Entering directory `/usr/src/ndiswrapper-1.6/driver'
make -C /lib/modules/2.6.12-9-powerpc/build SUBDIRS=/usr/src/ndiswrapper-1.6/driver \
        DRIVER_VERSION=1.6
/usr/src/linux-headers-2.6.12-9-powerpc/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-powerpc/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-powerpc'
  CC [M]  /usr/src/ndiswrapper-1.6/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/usr/src/ndiswrapper-1.6/driver/hal.o] Error 127
make[2]: *** [_module_/usr/src/ndiswrapper-1.6/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-powerpc'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.6/driver'
make: *** [all] Error 2

**************snip**************

I get the same result when I do the make as root.

I don't find gcc-3.4 among the software packages loaded or available to me in the synaptic package manager.  Since I am still a little unsure about all these GUIs, I also did a find as root and ... no gcc-3.4.

Any suggestions?  Am I on the right track for getting my wireless network card recognized by ubuntu?

---

### Post by bananana on 2005-12-02
Try apt-get install gcc-3.4

You will also probably need build-essential and linux-headers.

Also, in case you already have ndiswrapper installed, clean it up:
[INDENT]# rmmod ndiswrapper
# apt-get remove ndiswrapper-modules ndiswrapper-utils
# cd /path/to/ndiswrapper-1.6/
# make uninstall[/INDENT]

You can also make debian packages, so that apt can manage them:
[INDENT]# make deb
# dpkg -i ndiswrapper-utils-* ndiswrapper-modules-*[/INDENT]

I hope this is the end of your troubles. I've been struggling with ndiswrapper/BCM4306 for days.

---

### Post by hw-tph on 2005-12-02
First off, ndiswrapper is [evil](http://acx100.sourceforge.net/ndis_cludge.html) and you should do whatever you can to avoid it. Vote with your wallet and don't buy any equipment from Broadcom or other companies that don't release the documentation needed to write drivers.

Second, ndiswrapper is for 386 and compatible systems. It *will not work* on a PPC system.


Håkan

---

### Post by pstoddard61 on 2005-12-02
Thanks for the important advice Hakan.  :D   Unfortunately that is the wireless card that came with my apple powerbook.  :( 

Pete

Hakan wrote:

First off, ndiswrapper is evil and you should do whatever you can to avoid it. Vote with your wallet and don't buy any equipment from Broadcom or other companies that don't release the documentation needed to write drivers.

Second, ndiswrapper is for 386 and compatible systems. It will not work on a PPC system.


Håkan[/QUOTE]

---

