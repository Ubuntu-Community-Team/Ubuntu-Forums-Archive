---
title: "Compile problems with ndiswrapper source"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2007-06-17
Hi guys,

I'm working with wieman01 to get my wireless card working under ndiswrapper for WPA. In order to get it working, he reckons I need to use a newer version of ndiswrapper than the one in the Dapper repos. Sadly, I get the following error when I checkinstall.

 ```
(Reading database ... 125312 files and directories currently installed.)
Unpacking ndiswrapper (from .../ndiswrapper_1.47-1_i386.deb) ...
dpkg: error processing /home/patrick/ndiswrapper-1.47/ndiswrapper_1.47-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.15-27-386/modules.alias', which is also in package linux-image-2.6.15-27-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/patrick/ndiswrapper-1.47/ndiswrapper_1.47-1_i386.deb

```

I have followed the instructions in the INSTALL file, and have compiled without major problems before. The only thing of note is:

```
patrick@inspiron-8200:~/ndiswrapper-1.47$   ls /lib/modules/`uname -r`/build
arch     crypto   include  kernel    mm              scripts   usr
block    drivers  init     lib       Module.symvers  security
cluster  fs       ipc      Makefile  net             sound

```

The INSTALL file says I should have a .config file. Not sure if this is relevant.

Any ideas?

Thanks,

mono.

---

### Post by wieman01 on 2007-06-17
Before you install from source, I would remove the existing "ndiswrapper" package through Synaptic. Then download the latest source code and compile it from scratch. Don't use the DEB archive if it gives you error messages.

---

### Post by wieman01 on 2007-06-17
You find the .tar ball here:

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148")

_**EDIT:**_
> sudo tar -xvf <file>.tar.gz
...to unzip the file. Preferrably in "/opt".

---

### Post by monomaniacpat on 2007-06-17
I have apt-get remove --purged ndiswrapper, and compiled with make and then used checkinstall. I downloaded a tarball from the sourceforge page. I don't think I got it from any deb archive.

---

### Post by wieman01 on 2007-06-17
> **monomaniacpat said:**
> I have apt-get remove --purged ndiswrapper, and compiled with make and then used checkinstall. I downloaded a tarball from the sourceforge page. I don't think I got it from any deb archive.
Alright... the error message confused me.

What happens when you load the driver now?

---

### Post by monomaniacpat on 2007-06-17
When I load what driver? ndiswrapper is not installed. The installation failed for the reason stated above.

---

### Post by wieman01 on 2007-06-17
> **monomaniacpat said:**
> When I load what driver? ndiswrapper is not installed. The installation failed for the reason stated above.
Dumb question but you get that error message when you compile from source?

---

### Post by monomaniacpat on 2007-06-17
Sorry. Maybe I picked an inaccurate title. I got the error after comiling and having tried to use checkinstall. Here's all the commands etc:

```
patrick@inspiron-8200:~/ndiswrapper-1.47$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrap per files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
patrick@inspiron-8200:~/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/patrick/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/patrick/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  LD      /home/patrick/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/patrick/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/patrick/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/patrick/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/patrick/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make[1]: Leaving directory `/home/patrick/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/patrick/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/patrick/ndiswrapper-1.47/utils'
patrick@inspiron-8200:~/ndiswrapper-1.47$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> ndiswrapper - wireless windows drivers
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@inspiron-8200 ]
1 -  Summary: [ ndiswrapper - wireless windows drivers ]
2 -  Name:    [ ndiswrapper ]
3 -  Version: [ 1.47 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ndiswrapper-1.47 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
make -C driver install
make[1]: Entering directory `/home/patrick/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/patrick/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
echo /lib/modules/2.6.15-27-386/misc
/lib/modules/2.6.15-27-386/misc
mkdir -p /lib/modules/2.6.15-27-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.15-27-386/misc
install: setting permissions for `/lib/modules/2.6.15-27-386/misc/ndiswrapper.ko': No such file or directory
/sbin/depmod -a 2.6.15-27-386 -b /
make[1]: Leaving directory `/home/patrick/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/patrick/ndiswrapper-1.47/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install: setting permissions for `/sbin/loadndisdriver': No such file or directory
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install: setting permissions for `/usr/sbin/ndiswrapper': No such file or directory
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo
install: setting permissions for `/usr/sbin/ndiswrapper-buginfo': No such file or dire ctory

NOTE: Windows driver configuration file format has changed since 1.5. You must re-inst all Windows drivers if they were installed before.
make[1]: Leaving directory `/home/patrick/ndiswrapper-1.47/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install: setting permissions for `/usr/share/man/man8/ndiswrapper.8': No such file or directory
install -m 644 loadndisdriver.8 /usr/share/man/man8
install: setting permissions for `/usr/share/man/man8/loadndisdriver.8': No such file or directory

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./ChangeLog
./INSTALL
./README

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package
[1]+  Stopped                 sudo checkinstall
```

---

### Post by wieman01 on 2007-06-17
I have just tried on my system and there were no error messages at all:
> cd /opt
> sudo tar -xvf ndiswrapper-1.47.tar.gz
> sudo make
> sudo make install
No error message whatsoever...

---

### Post by wieman01 on 2007-06-17
Could it have to do with the kernel version again?

---

### Post by kevdog on 2007-06-17
It looks like you are trying to install over an existing installation.  I would first uninstall everything if this is the case (both through synaptic) and using the instructions here:[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

My kernel module is located at:
/lib/modules/`uname -r`/misc

---

### Post by monomaniacpat on 2007-06-17
It's possible. In the install file is says:

> You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory.

```
patrick@inspiron-8200:~$ uname -r
2.6.15-27-386

```

I have linux-headers-2.6.15-27-386

I expect if I used make install it would work, as the problem is with installing the package.

However, I don't want to be stuck with the program if I need to uninstall it at a later date. Which I understand is a problem with make install. Should I do it anyway?

EDIT: those instructions link to a list of cards supported...

---

### Post by wieman01 on 2007-06-17
Is your card listed there? Great link!

I could remove "ndiswrapper" by doing:
> sudo make uninstall
No problems here.

---

### Post by kevdog on 2007-06-17
What version of ndiswrapper are you trying to install.  Ive installed the most recent tarball (1.47 I think) and from svn, and both work no problem.

You have the linux headers great.
If you have the build-essential package installed also, that is basically all you need to do for compilation.

After making sure all previous installations are cleaned out (very important or you will find out later), in the ndiswrapper source directory

make distclean
make
sudo make install

You can check if the installation was a success with
ndiswrapper -v

If you get any message that hints of an error or something not quite right you will see (often caused by not totally removing old installations!)

You need to then install the driver file
sudo ndiswrapper ****.inf

and then insert ndiswrapper into kernel
sudo depmod -a
sudo modprobe ndiswrapper

You can check dmesg to see if this process was successful

A couple of other modifications to either /etc/iftab and /etc/network/interfaces may also need to be done.

If you want module loaded at startup you also need command
sudo ndiswrapper -m

Thats all there is to it

Reboot and all should (cross your fingers) be good!

---

### Post by monomaniacpat on 2007-06-17
Yes, WPC11 v.4 is listed under L.

So Are you saying I should just use make install? Where can I use make uninstall - only from the make directory?

EDIT: following kevdog's instructions...

When I tried to remove ndiswrapper with apt, before, I got a statement saying /etc/ndiswrapper was not removed because it contained files - should I remove it and if so, with what command?

---

### Post by monomaniacpat on 2007-06-17
OK, I've followed all those instructions and no complaints from the terminal.

When I enter:

```
patrick@inspiron-8200:~$ ndiswrapper -l
net8180 : driver installed
        device (10EC:8180) present (alternate driver: r818x)

```

All looks good.

I suppose I may as well reboot, even if it'll most likely end in a lockup.

---

### Post by kevdog on 2007-06-17
If you even in the past tried to install ndiswrapper from a repository, then you need to remove it with either apt or synaptic.  If you never installed from repository then you do not need to do this.

If you tried installing from source before now, then you need to uninstall with
sudo modprobe -r ndiswrapper
sudo niswrapper -r ***.inf

Then from source directory type make uninstall.

These instructions are all listed here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

Please read them thoroughly.  This is where I am getting my instructions.

---

### Post by wieman01 on 2007-06-17
> **monomaniacpat said:**
> OK, I've followed all those instructions and no complaints from the terminal.

When I enter:

```
patrick@inspiron-8200:~$ ndiswrapper -l
net8180 : driver installed
        device (10EC:8180) present (alternate driver: r818x)

```

All looks good.

I suppose I may as well reboot, even if it'll most likely end in a lockup.
Don't forget modprobing, etc. (see previous thread). Otherwise won't be loaded at boot.

---

### Post by kevdog on 2007-06-17
Ok you wrapped you driver inside of ndiswrapper, but you are not done yet.  You need to insert ndiswrapper in the kernel, and then maybe alter some other files.

---

### Post by monomaniacpat on 2007-06-17
OK. I'm writing this with the ethernet unplugged and the link light on my wireless card lit. I guess this means I have a working WPA connection!

Thanks for your help kevdog. I already sorted out network interfaces. I have, of course, modprobed etc.

I can't believe it's working!

Major thanks to wieman01 - you're by far the most helpful HOWTO writer I've come across!

---

### Post by wieman01 on 2007-06-17
> **monomaniacpat said:**
> OK. I'm writing this with the ethernet unplugged and the link light on my wireless card lit. I guess this means I have a working WPA connection!

Thanks for your help kevdog. I already sorted out network interfaces. I have, of course, modprobed etc.

I can't believe it's working!

Major thanks to wieman01 - you're by far the most helpful HOWTO writer I've come across!
My pleasure, buddy, my pleasure. I just paid it forward. ;-)

---

