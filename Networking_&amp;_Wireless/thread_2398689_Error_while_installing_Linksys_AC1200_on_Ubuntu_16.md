---
title: "Error while installing Linksys AC1200 on Ubuntu 16.04"
date: 2018-08-15
forum: Networking &amp; Wireless
---

### Post by carletonw on 2018-08-15
I've seen several posts where this is working but I'm not having same success even though I'm following instructions from other posts:

I've already completed the following.  But when I try to build and install, I get: (bad exit status:2)  ...  ideas?  Thanks in advance

sudo apt-get update
sudo apt-get install git dkms
git clone  [https://github.com/ptpt52/rtl8812au.git](https://github.com/ptpt52/rtl8812au.git)
cd rtl8812au
sudo make -f Makefile.dkms install
sudo modprobe rtl8812au

>>>  results of make and install <<<<

[FONT=arial]carleton@carleton-OptiPlex-755:~/rtl8812au$ sudo make -f Makefile.dkms install[/FONT]
[FONT=arial]make clean[/FONT]
[FONT=arial]make[1]: Entering directory '/home/carleton/rtl8812au'[/FONT]
[FONT=arial]make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-32-generic/build M=/home/carleton/rtl8812au clean[/FONT]
[FONT=arial]make[2]: Entering directory '/usr/src/linux-headers-4.15.0-32-generic'[/FONT]
[FONT=arial]make[2]: Leaving directory '/usr/src/linux-headers-4.15.0-32-generic'[/FONT]
[FONT=arial]make[1]: Leaving directory '/home/carleton/rtl8812au'[/FONT]
[FONT=arial]mkdir -p '/usr/src/rtl8812au-4.3.14'[/FONT]
[FONT=arial]cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'[/FONT]
[FONT=arial]cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'[/FONT]
[FONT=arial]sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'[/FONT]
[FONT=arial]dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true[/FONT]
[FONT=arial]dkms build -m rtl8812au -v 4.3.14[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Kernel preparation unnecessary for this kernel.  Skipping...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Building module:[/FONT]
[FONT=arial]cleaning build area....[/FONT]
[FONT=arial]make KERNELRELEASE=4.15.0-32-generic KVER=4.15.0-32-generic......(bad exit status: 2)[/FONT]
[FONT=arial]ERROR (dkms apport): binary package for rtl8812au: 4.3.14 not found[/FONT]
[FONT=arial]Error! Bad return status for module build on kernel: 4.15.0-32-generic (x86_64)[/FONT]
[FONT=arial]Consult /var/lib/dkms/rtl8812au/4.3.14/build/make.log for more information.[/FONT]
[FONT=arial]Makefile.dkms:18: recipe for target 'build' failed[/FONT]
[FONT=arial]make: *** [build] Error 10[/FONT]

---

### Post by praseodym on 2018-08-17
Why not
```

sudo apt-get install rtl8812au-dkms
```

---

### Post by carletonw on 2018-08-19
I tried that and still get the following when I run the make file:

carleton@carleton-OptiPlex-755:~/rtl8812au$ sudo apt-get install rtl8812au-dkms
[sudo] password for carleton: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu2).
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-29 linux-headers-4.15.0-29-generic linux-image-4.15.0-24-generic linux-image-4.15.0-29-generic
  linux-modules-4.15.0-24-generic linux-modules-4.15.0-29-generic snap-confine
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.



carleton@carleton-OptiPlex-755:~/rtl8812au$ sudo make -f Makefile.dkms install
make clean
make[1]: Entering directory '/home/carleton/rtl8812au'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-32-generic/build M=/home/carleton/rtl8812au clean
make[2]: Entering directory '/usr/src/linux-headers-4.15.0-32-generic'
make[2]: Leaving directory '/usr/src/linux-headers-4.15.0-32-generic'
make[1]: Leaving directory '/home/carleton/rtl8812au'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true
dkms build -m rtl8812au -v 4.3.14


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
make KERNELRELEASE=4.15.0-32-generic KVER=4.15.0-32-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8812au: 4.3.14 not found
Error! Bad return status for module build on kernel: 4.15.0-32-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.14/build/make.log for more information.
Makefile.dkms:18: recipe for target 'build' failed
make: *** [build] Error 10

---

### Post by praseodym on 2018-08-20
If the package is installed there is no need to compile. Tried deactivating SecureBoot?

---

### Post by carletonw on 2018-08-25
My Dell is too old and doesn't have SecureBoot.  Any other ideas?  Thanks

---

### Post by praseodym on 2018-08-25
BIOS reset?

---

### Post by carletonw on 2018-09-01
Before I reset my BIOS. help me understand how that will help when it actually looks like the package was never built.  See the whole sequence below.  I'm sure I don't understand why after makefile failure ( binary package not found)...  I'm assuming that something unrelated to BIOS is causing package make to fail....

See sequence below.  I appreciate any training / explanation I need to understand how that relates to BIOS issues.  Thanks for your continued help!

[COLOR=#000000][INDENT]carleton@carleton-OptiPlex-755:~/rtl8812au$ sudo make -f Makefile.dkms install
make clean
make[1]: Entering directory '/home/carleton/rtl8812au'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-32-generic/build M=/home/carleton/rtl8812au clean
make[2]: Entering directory '/usr/src/linux-headers-4.15.0-32-generic'
make[2]: Leaving directory '/usr/src/linux-headers-4.15.0-32-generic'
make[1]: Leaving directory '/home/carleton/rtl8812au'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true
dkms build -m rtl8812au -v 4.3.14


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area....
[COLOR=#ff0000]make KERNELRELEASE=4.15.0-32-generic KVER=4.15.0-32-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8812au: 4.3.14 not found[/COLOR]
Error! Bad return status for module build on kernel: 4.15.0-32-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.14/build/make.log for more information.
Makefile.dkms:18: recipe for target 'build' failed
make: *** [build] Error 10[/INDENT]


[/COLOR]

---

### Post by jeremy31 on 2018-09-01
The source you have likely isn't patched for the 4.15 kernel, post results for ```
lsusb
```

---

### Post by praseodym on 2018-09-02
[https://github.com/gordboy/rtl8812au](https://github.com/gordboy/rtl8812au)

What about this one?

---

### Post by carletonw on 2018-09-09
Praseodym, That repository worked!  Thanks for your help!

---

