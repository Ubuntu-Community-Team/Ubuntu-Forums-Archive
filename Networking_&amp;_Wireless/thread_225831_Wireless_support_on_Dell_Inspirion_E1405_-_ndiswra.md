---
title: "Wireless support on Dell Inspirion E1405 - ndiswrapper"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by hawkbane on 2006-07-30
I recently purchased a referb Dell from Dell Outlet for the purpose of taking notes in class during the upcoming school year.  Everything works fine except for the wireless card.  I have been attempting to follow the instructions on the ndiswrapper wiki [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation").  However, I have been foiled from the beginning.  I have determined that my kernel version is 2.6.15-26-386 and that I have the source and headers installed though apt-get.  When I try to run the ndiswrapper 'make' I get the following error:

> 
make -C driver
make[1]: Entering directory `/home/hawkbane/Desktop/ndiswrapper-1.21/driver'Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/hawkbane/Desktop/ndiswrapper-1.21/driver'
make: *** [all] Error 2


According to ndiswrapper wiki, I need to run the command:
> 
ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build


I cannot get this to work right to create the symbolic link to the right directory location.  Can anyone help me?  The only other useful thing I think I can provide is the directory listing of my /usr/src/ dir:
> 
kernel-build-2.4.27-2            kernel-headers-2.4.27-2-k7-smp
kernel-headers-2.4.27-2          kernel-source-2.4.27.tar.bz2
kernel-headers-2.4.27-2-386      linux-headers-2.6.15-23
kernel-headers-2.4.27-2-586tsc   linux-headers-2.6.15-23-386
kernel-headers-2.4.27-2-686      linux-headers-2.6.15-26
kernel-headers-2.4.27-2-686-smp  linux-headers-2.6.15-26-386
kernel-headers-2.4.27-2-k6       linux-source-2.6.15.tar.bz2
kernel-headers-2.4.27-2-k7


Thanks for any help you guys can give me!

---

### Post by MarkSheely on 2006-07-30
There's a much easier way to go about this.

First off, which wireless card does the 1405 have?  Is it the Intel pro wireless 3945?

--Mark

---

### Post by hawkbane on 2006-07-31
No, it is the crappy  Wireless 1390.  I know others have had success getting this to work with ndiswrapper, but I can't get that symbolic link established so I can install the driver.  Thanks for your help!  An easy solution would be great.

---

### Post by MarkSheely on 2006-07-31
Oh no. Not *that* card.  I was wrong, there really isn't an easier way to go about this.  

Let's focus on the symbolic link then.  Do you get an error message of some sort, or is it a situation where you enter the code to create the link 
(ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build), and then nothing works as it should when you proceed from that point?

And, not to be insulting, but are you sure you have entered the code correctly, without extra/missing spaces or anything?

-Mark

---

### Post by hawkbane on 2006-08-02
Mark,

I do not get an error message creating the link.  Here is exactly what I have done:

According to the error message that I get when I try to 'make' ndiswrapper I get the error message (as above), 
> make -C driver
make[1]: Entering directory `/home/hawkbane/Desktop/ndiswrapper-1.21/driver'Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
give the path to kernel build directory with
KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/hawkbane/Desktop/ndiswrapper-1.21/driver'
make: *** [all] Error 2

From reading this error message, I can see that ndiswrapper is trying to find the kernel source associated to **/lib/modules/2.6.15-26-386/build**.  I then proceeded to use Synaptic to double check that my kernel source was installed.  After confirming this, I set about trying to get the example command from ndiswrapper's wiki to work the:
> ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

However, this is what confuses me.  The example command tells me that my kernel source will be located in */usr/src/linux-<kernel-version>*.  There is no directory with naming convention (reference above for a directory listing of my /usr/src/ directory).  I have experimented with making the symbolic link with several of the directories, and the link is made without errors, but when I go to compile ndiswrapper, I always get the same error messages.  

If you can tell from looking at that directory printout which directory I need, I would be extremely grateful.  I would not consider myself a total noob, but I am nowhere near elite either.  I have used various distros of Linux as my main desktop OS on and off again for several years, but this is just my first time having to perform this particular function.  

Thanx for any info you can give!
~Hawkbane

---

### Post by hawkbane on 2006-08-07
Well, there has been some progress made, but I am not yet out of the woods.  I have my kernel source extrated from the .tar.bz2 into /usr/src/ and have the symbolic link established and working fine.  Now when I execute 'make' in the ndiswrapper directory, it does begin to build the program.  However, since there does not appear to be (from searching the forums) any external module support in the 2.6.15 kernel, the compile bombs out with the error: 
> make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
/bin/sh: scripts/mod/modpost: No such file or directory
make[3]: *** [__modpost] Error 127
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/hawkbane/Desktop/ndiswrapper-1.22/driver'
make: *** [all] Error 2
Anybody have any ideas on how to fix this?  I have heard rumors thoughout the forums that there is a patch, but no-one seems to know where it is on the web or how to install it.  

Once again, any info you guys are willing to share would be most excellent.

Party on, dudes!
~Hawkbane

---

