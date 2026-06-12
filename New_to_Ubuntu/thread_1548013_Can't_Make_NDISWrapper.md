---
title: "Can't Make NDISWrapper"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Jaiichi on 2010-08-07
I recently bought a Netbook (Samsung NB30) and installed UNE 10.04 on it. My wireless is Disabled, so I tried to install NDISWrapper to use the drivers, but when I went to Make it, it seemed to fail and many of the lines came out with "not found" or "Error 2".

Here's the terminal dump after I tried to make it

> make -C driver
make[1]: Entering directory `/home/ian/Downloads/src/ndiswrapper-1.56/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.32-21-generic M=/home/ian/Downloads/src/ndiswrapper-1.56/ndiswrapper-1.56/driver
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[2]: gcc: Command not found
  LD      /home/ian/Downloads/src/ndiswrapper-1.56/ndiswrapper-1.56/driver/built-in.o
/bin/sh: ar: not found
make[3]: *** [/home/ian/Downloads/src/ndiswrapper-1.56/ndiswrapper-1.56/driver/built-in.o] Error 127
make[2]: *** [_module_/home/ian/Downloads/src/ndiswrapper-1.56/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ian/Downloads/src/ndiswrapper-1.56/ndiswrapper-1.56/driver'
make: *** [all] Error 2

---

### Post by ajgreeny on 2010-08-07
Are you sure you need ndiswrapper, and if you really do, why bother to compile it; it's much easier to use ndisgtk from the repos, which you should be able to use if you temporarily use a cable connection, or if necessary download the package and dependencies on another computer.  You can get the dependencies list simply from trying to install with **synaptic ->File ->Save markings as** (yes, I realise synaptic will not be able to download without a connection) and save as a txt file listing.

[http://packages.ubuntu.com/lucid/ndisgtk](http://packages.ubuntu.com/lucid/ndisgtk)

---

### Post by WelshChris on 2010-08-07
Not much experience with make, but is it saying that gcc or ar can't be found?  If so, install them.  Can't be that simple, though.  Like I said, haven't had much to do with make for years =)

---

