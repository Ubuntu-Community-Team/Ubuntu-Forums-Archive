---
title: "[SOLVED] Installing ndiswrapper manually via packages"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-11
I am helping a friend with a clean Feisty install from a Canonical CD on a Toshiba Satellite 1905-s304. A laptop.

We are trying to get wireless connectivity up and running.

When the laptop had XP, it reached the 'net via a Linksys WUSB 11v4 adapter.

Once Feisty was installed, there was the panel icon for wired, but not wireless connectivity.

I know I will need ndiswrapper and the liinksys driver/s for this. As I have installed them on my desktop dell and it's working very smoothly.

I see from:

WifiDocs/Driver/Ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

under

2.2. With Internet access on another computer

      If you do not have a working Internet connection, you can use another computer which is connected to the Internet to download the following packages.

2.2.1. Feisty Fawn (7.04) and Edgy Eft (6.10)

      For 7.04 Feisty Fawn
         1.            [WWW] [http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
         2.            [WWW] [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
         3.            [WWW] [http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk)

I have downloaded these 3 files and put them on a thumb-drive. 

BUT from near the beginning of the WifiDocs/Driver/Ndiswrapper I see:

**"These instructions do not apply to Ubuntu for Power PC (PPC) and the Ubuntu Desktop CDs."**

As the harddisk was wiped when Feisty was installed and as the above sentence indicates that you MUST use the:

"These instructions apply only when using the x86 Alternate CD"
[B]
Is there a workaround?[/B] or does that language apply to some other installation of the ndiswrapper?


Below are the suggested posts I received while entering this post's Title. 

I looked at 3 of them and couldn't find a similarity.


Un-installing Packages Manually  	Graham1  	General Help  	2  	May 25th, 2007 01:50 PM
Manually Downloading/Installing Packages 	lemboy4 	Absolute Beginner Talk 	3 	March 17th, 2007 11:48 PM
Installing packages manually 	itrevorevans 	Installation & Upgrades 	3 	January 22nd, 2007 10:31 AM
Help on installing packages manually 	breeky5 	Absolute Beginner Talk 	9 	August 11th, 2006 10:48 AM
Manually installing packages 	That Other Guy 	Absolute Beginner Talk 	3 	August 2nd,

---

### Post by kevdog on 2007-07-11
I think I helped you originally install ndiswrapper from source.  Although there probably will not be a problem installing the deb files you downloaded, I would again recommend installing ndiswrapper from source as I did with you.  Its much more reliable.  The ndisgtk package in my humble opinion "is worthless", so the package installation isnt really going to by you a GUI.

---

### Post by Mark_in_Hollywood on 2007-07-11
I would gladly install the files from a "source", but have no access to the internet on this laptop. The wireless won't work, obviously for lack of a ndiswrapper.

WvDial can't find the built-in dial-up modem because it's a soft-modem. I would attach my old external modem, but the laptop has no serial port, only usb, firewire, and ethernet (and built-in dial-up modem).

Kevdog, what does "buy you a gui" have to do it it? And yes, I'm the same guy as yesterday or the day before. Still trying to get it all to work. I was ready to follow the instructions you previously provided, but wanted to make sure that:

first -- do no harm

was and is my Motto.

---

### Post by kevdog on 2007-07-11
Do the following to install from source

You need the Ubuntu installation CD and get the ndiswrapper-1.47.tar.gz file from: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

You are gong to have to transfer the tar.gz file via USB stick from another computer to Ubuntu

Then do the following:
1. Stick ubuntu cd into drive wait to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

Then transfer the tar.gz file into some directory
cd "Whatever directory the tar.gz file is in"
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Ok ndiswrapper should be installed
check with 
ndiswrapper -v

Thats it -- Simple

---

### Post by Mark_in_Hollywood on 2007-07-11
Then do the following:
1. Stick ubuntu cd into drive wait to become ready

Does the ubuntu cd have to boot first?


The feisty simply doesn't find the canonical cd once gnome (& everything else) is up.

Jeeeeezzzzz!

---

### Post by kevdog on 2007-07-11
No boot into feisty 

Wait for gnome and everything to be ready

Stick Ubuntu installation CD into drive -- drive will spin, but it should also automount and a icon should appear on your desktop.

Then type at a command prompt
sudo cd-rom add

etc.

---

### Post by Mark_in_Hollywood on 2007-07-11
No sir:

Boot with canonical cd-rom in drive.

No icon appears.

Places/Computer/CD-RW--DVD-ROM 

highlited and right clicked: mount volume:

response:

unable to mount volume, "probably" no media in drive

yuttzzz!

---

### Post by kevdog on 2007-07-11
Try another  CD or burn another one,  it could be bad or something

---

### Post by Mark_in_Hollywood on 2007-07-11
Roger Wilco,

but the cd in the drive is the cd that was used to install feisty on the laptop's harddisk!

---

### Post by Mark_in_Hollywood on 2007-07-11
Another CD, only full of .pdf files is also a boat anchor.

Asking the drive to mount returned the same message as before: probably no media

---

### Post by kevdog on 2007-07-11
Cant explain that one!

---

### Post by Mark_in_Hollywood on 2007-07-13
Kevdog.

I hope you are still with me. The combo drive is not going to work under feisty. Something to do with the kernel and grub. 

I have deprecated to Edgy. Drive is working.

I'm following your post about

download ndiswrapper-1.47 from source and thumb drive it to laptop. DONE. Using archive manager, the .tar.gz is opened and files in directory ndiswrapper-1.47


Then do the following:

1. Stick ubuntu cd into drive wait to become ready **[done]**

2. sudo apt-cdrom add[B] [done and ubuntu 6.06 i386 is on desktop]
[/B]

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

Then transfer the tar.gz file into some directory
cd "Whatever directory the tar.gz file is in"

tar -zxvf ndiswrapper-1.47.tar.gz **[done]**

cd ndiswrapper-1.47 **[done]**


make distclean **[returned**

james@Maplewood:~/ndiswrapper-1.47$ make distclean
make -C driver clean
make[1]: Entering directory `/home/james/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
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
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
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

and nothing worked after that

where do I go from here?

sudo make install

Ok ndiswrapper should be installed
check with
ndiswrapper -v

---

### Post by fredj on 2007-07-13
Sometimes CDs can be marginal and don't mount properly so its worth trying ejecting the CD and trying 
again.
The build-essential package installs a C++ compiler and everything you need to compile source files.
However I don't think that build-essential is on the live CD and I don't think its on the alternate CD either.
It may be on the full DVD. Could someone please comment on this.
Does your computer have a wired network card and does your wireless router have wired ports on the back
as well. If so you could try using a long internet cable to connect this way instead.
There is a version of ndiswrapper on the CD which you can install through the System->Administration->
synaptic package manager. This may work with some wireless network cards and the latest WinXP
drivers. However this version of ndiswrapper often appears to work but doesn't because the wrong files
have been put in the repositories (a carry over from Edgy it seems). So the only guaranteed solution is
to get the latest source for ndiswrapper and compile it once you have installed the build-essential package.
On the whole not a good situation for beginners to have to face and not the best introduction to Ubuntu.

---

### Post by theer on 2007-07-16
I follow the introduction of how to installing ndiswrapper-1.47 in tar.gz 
the problem I found is there is no include files like <stdio.h> or else things.
Does it have "C++ compiler" in Ubuntu desktop? 
I want to know where I can find and install the compiler

---

### Post by kevdog on 2007-07-16
To use the c++ compiler you will need the build essential package installed.  I think this was covered earlier in the thread??

---

