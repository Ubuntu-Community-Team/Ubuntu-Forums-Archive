---
title: "[SOLVED] Missing 'include' and '.config' in ndiswrappter"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-13
I downloaded ndiswrapper from sourceforge. It is the latest stable ver. 1.47.

I right clicked and opened with archive-manager.

Files spilled out into ndiswrapper-1.47

a readme file INSTALL says I should have in /lib/modules/2.6.15-23-386 two items:

include

and

.config

I see neither.

This is a dapper install on a Toshiba Satellite 1905-s304, that is less than 1 hour old. 

Anybody?

---

### Post by kevdog on 2007-07-13
Maybe that is the case, but if you just want to compile and install ndiswrapper you dont need those files anyway.  Just go into the directory

make distclean
make

Before you install, ensure any previous versions have been removed.  If this is a new installation, then you probably dont have any old files

sudo make install

Check with 
ndiswrapper -v

---

### Post by Mark_in_Hollywood on 2007-07-13
Kevdog. 

I'm following your post about

download ndiswrapper-1.47 from source and thumb drive it to laptop.** DONE**. Using archive manager, the .tar.gz is opened and files in directory ndiswrapper-1.47


Then do the following:

1. Stick ubuntu cd into drive wait to become ready **[done]**

2. sudo apt-cdrom add **[done and ubuntu 6.06 i386 is on desktop]**


3. sudo aptitude update returned:

james@Maplewood:~/ndiswrapper-1.47$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done

I took this to be non-critical and proceeded to:

4. sudo aptitude install build-essential

which I think reported no errors, but I've lost that bit.

Then transfer the tar.gz file into some directory cd "Whatever directory the tar.gz file is in"

tar -zxvf ndiswrapper-1.47.tar.gz** [done]**

cd ndiswrapper-1.47 **[done]**


make distclean** [returned**

james@Maplewood:~/ndiswrapper-1.47$ make distclean
make -C driver clean
make[1]: Entering directory `/home/james/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
divdi3.o workqueue.o .*.ko.cmd .*.o.cmd compat.h \
ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/james/ndiswrapper-1.47/driver'
make -C utils clean
make[1]: Entering directory `/home/james/ndiswrapper-1.47/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/james/ndiswrapper-1.47/utils'
rm -f *~
rm -fr ndiswrapper-1.47 ndiswrapper-1.47.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/james/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
divdi3.o workqueue.o .*.ko.cmd .*.o.cmd compat.h \
ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/james/ndiswrapper-1.47/driver'
make -C utils distclean
make[1]: Entering directory `/home/james/ndiswrapper-1.47/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/james/ndiswrapper-1.47/utils'
rm -f .\#*

make **[returned]**

james@Maplewood:~/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/james/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
give the path to kernel build directory with
KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/james/ndiswrapper-1.47/driver'
make: *** [all] Error 2
james@Maplewood:~/ndiswrapper-1.47$

[B]and nothing worked after that

where do I go from here?[/B]

sudo make install

Ok ndiswrapper should be installed
check with
ndiswrapper -v

---

### Post by kevdog on 2007-07-13
Put CD back into driver

sudo aptitude install linux-headers-`uname -r`

Then go back into the ndiswrapper directoy
make distclean
make
sudo make install

---

### Post by Mark_in_Hollywood on 2007-07-13
Done deal. Now back to installing the WUSB 11v4 for wireless on this (now) deprecated Dapper.

---

### Post by kevdog on 2007-07-13
Why Dapper instead of Feisty??

---

### Post by Mark_in_Hollywood on 2007-07-13
You may not remember, I'm the fellow with a friend's Toshiba laptop (1905-s304) which I had installed Feisty on, only to lose the use of both the combo DVD-ROM/CD-RW and the floppy. I've spend since day-before-yesterday getting that fixed.

I've gotten back to downloading the linksys driver, putting it on the laptop's harddisk, unzipping it and got to your last instruction:

Check if installed properly:
ndiswrapper -l

report any errors.

Errors follow:

ls: /etc/ndiswrapper: No such file or directory

a little more help, please.

---

### Post by kevdog on 2007-07-13
Please post the following
ndiswrapper -v

Did you install the driver like:
sudo ndiswrapper -i ******.inf <---With .inf and .sys files in same directory

Have to say of the thousands of errors people have thrown my way, this is a first.

---

### Post by Mark_in_Hollywood on 2007-07-13
james@Maplewood:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.15-23-386/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0

---

### Post by kevdog on 2007-07-13
Ok, that looks great

What about
ndiswrapper -l

And did you try installing the driver??? When you did you had to get something back.

---

### Post by Mark_in_Hollywood on 2007-07-13
from

james@maplewood:~$ ndiswrapper -l

returns:

ls: /etc/ndiswrapper: No such file or directory

---

### Post by kevdog on 2007-07-13
What about sudo ndiswrapper -l??? Did you get any message when you installed the driver?

---

### Post by Mark_in_Hollywood on 2007-07-13
sudo ndiswrapper -l 

returns the same message as though no sudo

When installed I didn't notice any errors.

I have tried the ndiswrapper -l from several directories/sub-directories and all I get is "No such file or directory"

---

### Post by kevdog on 2007-07-13
You ever get that feeling like your banging your head against a wall!!!!!!!

This is the last time I'm going to ask --- did you install the driver via sudo ndiswrapper -i ***.inf??? If you did, did you get a message???

Out

---

### Post by Mark_in_Hollywood on 2007-07-13
I'm so sorry, I'm a little stressed and not thinking clearly.

Yes: it was installed with sudo

---

### Post by Mark_in_Hollywood on 2007-07-13
james@Maplewood:~/wusb/WUSB11/Drivers$ sudo ndiswrapper -i WUSB11V4.inf
Password:
installing wusb11v4 ...
couldn't open WUSB11V4.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
james@Maplewood:~/wusb/WUSB11/Drivers$

---

### Post by kevdog on 2007-07-13
What's in your ~/wusb/WUSB11/Drivers directory??

Report output of:
ls

---

### Post by Mark_in_Hollywood on 2007-07-13
james@Maplewood:~/wusb/WUSB11/Drivers$ ls
LSPMUSB.cat  mdusb.out     PRISM9x.SYS   VNETUSBA.SYS
LSPMUSB.inf  netrfm2k.cat  PRISMXP.SYS   vnetusbl.sys
LSPMUSB.sys  NETUSB.inf    vnet58l.sys   vnetusbxp.sys
m4301a.cat   NETUSB.SYS    vnet58lx.sys  WINXP
M4301A.sys   NETUSBXP.SYS  vnetu9xl.sys  WUSB11v4.inf
james@Maplewood:~/wusb/WUSB11/Drivers$

---

### Post by kevdog on 2007-07-13
Where is the corresponding .sys file for the WUSB11v4.inf file??? It doesnt have to be the same name -- but from all those files you listed Im not sure what the corresponding file for inf file is.

---

### Post by Mark_in_Hollywood on 2007-07-13
Two things:

I found:

james@Maplewood:~/wusb/WUSB11/Drivers$ ndiswrapper -l
wusb11v4 : invalid driver!
james@Maplewood:~/wusb/WUSB11/Drivers$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.15-23-386/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0
james@Maplewood:~/wusb/WUSB11/Drivers$

and the .sys files are what are in that directory.

This is the exact same setup we (you more than I) did earlier this week. After following your instructions in a different post, even though the very last command didn't "work", the wireless adapter started working and has since.

I'm sorry if I'm slow or not good at this. It's too "new" to me.

---

### Post by kevdog on 2007-07-13
Congratulations!

---

