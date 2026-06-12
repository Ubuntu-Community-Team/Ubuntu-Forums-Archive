---
title: "need help compiling ndiswrapper"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by 0okami on 2006-08-18
im not quite sure what this means: 

```

http://ndiswrapper.sourceforge.net/wiki

Prerequisites 
=============

You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.
```

surely its the reason im getting this error: 
```
ookami@navi-001:~/Desktop/ndiswrapper-1.23$ sudo make install
make -C driver install
make[1]: Entering directory `/home/ookami/Desktop/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/ookami/Desktop/ndiswrapper-1.23/driver'
make: *** [install] Error 2
ookami@navi-001:~/Desktop/ndiswrapper-1.23$ echo linux-headers-$(uname -r)
linux-headers-2.6.15-26-386
ookami@navi-001:~/Desktop/ndiswrapper-1.23$

```

not quite sure what to do next.... so, if anyone has any info or help, i'd greatly appreciate it.

im using dapper.

---

### Post by mpvano on 2006-08-18
I know this sounds like I'm giving you a hard time, but....

Why do you think you need to compile ndiswrapper?

For nearly all hardware, the version already BUILT-IN to dapper works fine!

Building drivers for current linux releases is not obvious or easy, and it definitely doesn't work the way many FAQ's describe (they're out of date or apply to different kernel setups than most "packaged" releases use).

Many people think that ndiswrapper is missing because there is a second package included with Ubuntu releases that you need to add from the Ubuntu repositories or installation disk in order to set it up. This is the case with many drivers. The package is called "ndiswrapper-utils" and contains several things including the program called "ndiswrapper" which is NOT the driver, but is needed to add your windows driver to the installation so that it can be used. You can check for its presence by typing "ndiswrapper" from a terminal session. It will complain, but if it runs, it's installed. If it's not installed use synaptic to install it.

A newer version of ndiswrapper will not normally help problems connecting to your access point with WEP, WAP, or dhcp issues. Those are usually caused by other configuration issues.

Hope this saves you some trouble. If you still need to build it from source, I can give you some pointers to how to do that, but would rather not further confuse this very confused subject unless you're sure you need them.

Mario

---

### Post by bensexson on 2006-08-18
You need to install the kernel headers for your kernel.  Check synaptic.

---

