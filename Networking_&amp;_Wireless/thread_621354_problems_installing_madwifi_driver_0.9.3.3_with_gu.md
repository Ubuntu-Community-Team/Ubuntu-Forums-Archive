---
title: "problems installing madwifi driver 0.9.3.3 with gutsy (7.10)"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by mad_shadow555 on 2007-11-23
Hi all,

I installed gutsy on a T42 IBM ThinkPad in a dual boot configuartion with XP.
I have a D-Link DWL-G650 Wireless card.
Ubuntu recognized it and I was able to connect to AP's. However, from time to time (maybe when changing modes from station to ad-hoc) the laptop just froze and I needed to do a hard reboot.

I decided to try and install the latest driver posted as stable on the madwifi.org site- 0.9.3.3.

After following all the instructions on the site, I got stuck on:
sudo modprobe ath_pci, i just get the following:

WARNING: Could not open '/lib/modules/2.6.22-14-generic/volatile/ath_hal.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/madwifi/wlan.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko': No such file or directory

I checked and indeed those files are missing.
It seems the sudo make and sudo make install commands created a directory "2.6.22.9" under /lib/modules in addition to the "2.6.22-14-generic" directory there.

so, I'm stuck. does anyone know why this happens?
do I have to compile the latest madwifi sources (although unstable)?

---

### Post by kevdog on 2007-11-23
What kernel versions are you using??  I would probably compile from scratch b/c the source compiles against the header files for your kernel.  Unfortunately with every kernel change (ie Feisty -> Gutsy -> Hardy), the modules will have to be recompiled against the new headers.  That is why they call such things such as madwifi, ndiswrapper custom kernel modules b/c they are modules compiled against the kernel.  Custom b/c they were not contained by default in the kernel

---

### Post by mad_shadow555 on 2007-11-24
I used the kernel that comes with gutsy.
uname -r says 2.6.22-14-generic.

I did compile the madwifi sources just as this tutorial says
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo"):

it's just the modprobe that's not working

---

### Post by kevdog on 2007-11-24
I know that you probably did this, however did you install the header files for your kernel version, ie

sudo aptitude install linux-headers-`uname -r`

---

### Post by OOzypal on 2007-11-24
Hello Guys/Gals,

I am joining the club. I have a problem installing the madwifi driver. Here is my 'make' output
```
hab@laptop {...2938-20071124}$ sudo make
[sudo] password for hab:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/hab/crack/madwifi-ng-r2938-20071124 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.o
cc1: warnings being treated as errors
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c: In function 'ath_intr':
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:1993: warning: unused variable 'ic'
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c: In function 'ath_tx_startraw':
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:2659: error: 'ic' undeclared (first use in this function)
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:2659: error: (Each undeclared identifier is reported only once
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:2659: error: for each function it appears in.)
make[3]: *** [/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.o] Error 1
make[2]: *** [/home/hab/crack/madwifi-ng-r2938-20071124/ath] Error 2
make[1]: *** [_module_/home/hab/crack/madwifi-ng-r2938-20071124] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```

---

### Post by kevdog on 2007-11-24
Have you downloaded the headers???  What happens if you type make rather than sudo make?

---

### Post by OOzypal on 2007-11-25
Yes I have the headers installed.

```
hab@laptop {...2938-20071124}$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/hab/crack/madwifi-ng-r2938-20071124 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.o
cc1: warnings being treated as errors
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c: In function 'ath_intr':
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:1993: warning: unused variable 'ic'
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c: In function 'ath_tx_startraw':
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:2659: error: 'ic' undeclared (first use in this function)
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:2659: error: (Each undeclared identifier is reported only once
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:2659: error: for each function it appears in.)
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c: At top level:
/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.c:11845: fatal error: opening dependency file /home/hab/crack/madwifi-ng-r2938-20071124/ath/.if_ath.o.d: Permission denied
compilation terminated.
make[3]: *** [/home/hab/crack/madwifi-ng-r2938-20071124/ath/if_ath.o] Error 1
make[2]: *** [/home/hab/crack/madwifi-ng-r2938-20071124/ath] Error 2
make[1]: *** [_module_/home/hab/crack/madwifi-ng-r2938-20071124] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

```

---

### Post by kevdog on 2007-11-25
I do have to say Im confiused why you cant compile madwifi.  Do you have a wired connection??

If you do can you try to install the svn version.

First

sudo aptitude install subversion

Then
cd ~
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
cd madwifi
make clean

I can remember if there is a config file, if there is
./config

Then
make

---

### Post by OOzypal on 2007-11-25
This is exactly what I did. I downloaded today's snapshot and it got complied ok.

---

### Post by kevdog on 2007-11-25
So everything is working?

---

