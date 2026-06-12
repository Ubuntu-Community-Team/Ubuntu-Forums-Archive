---
title: "IEEE80211 problem"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by polkovnik on 2007-07-22
Hi all :)

I am new to Ubuntu.
I've got Intel 3945 ABG Wireless adapter. It should work out of the box. I didn't know that and tried to install the driver and the most recent ieee80211 version. Ieee seems to be installing ok, but ipw3945 doesn't want - it thinks that ieee is not installed properly. 

Then I found out how easy should be the installation process, but it was too late - I did smth bad - now when I only  turn on the wireless the computer dies.

Is there any possibility to get back the old ieee80211 version? What can I do?

**Here is the quote from terminal when I am installing ieee:**

iaroslav@iaroslav-laptop:~/wpa$ cd ieee80211-1.2.18
iaroslav@iaroslav-laptop:~/wpa/ieee80211-1.2.18
$ sudo make
Password:
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.20-15-generic for ieee80211 components...
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-15-generic/include/net/ieee80211_radiotap.h
/lib/modules/2.6.20-15-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.20-15-generic/include/net/ieee80211.h
Above files found.  Remove? [y],n y
make -C /lib/modules/2.6.20-15-generic/build M=/home/iaroslav/wpa/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:17: 
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:21: 
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'


iaroslav@iaroslav-laptop:~/wpa/ieee80211-1.2.18$ sudo make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.20-15-generic/build M=/home/iaroslav/wpa/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:17: 
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/iaroslav/wpa/ieee80211-1.2.18/Makefile:21: 
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
install -d /lib/modules/2.6.20-15-generic/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.20-15-generic/net/ieee80211/
install -d `echo /lib/modules/2.6.20-15-generic/include | grep "/net\$" || echo /lib/modules/2.6.20-15-generic/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.20-15-generic/include | grep "/net\$" || echo /lib/modules/2.6.20-15-generic/include/net`
mkdir -p /lib/modules/2.6.20-15-generic/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.20-15-generic/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.20-15-generic

**Then I am trying to install ipw3945-1.2.0:**

iaroslav@iaroslav-laptop:~/wpa/ieee80211-1.2.18$ cd ..
iaroslav@iaroslav-laptop:~/wpa$ cd ipw3945-1.2.0
iaroslav@iaroslav-laptop:~/wpa/ipw3945-1.2.0$ sudo make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1


**If I use IEEE80211_IGNORE_DUPLICATE=y it answers:**

iaroslav@iaroslav-laptop:~/wpa/ipw3945-1.2.0$ sudo make IEEE80211_IGNORE_DUPLICATE=y
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.20-15-generic/include/ /lib/modules/2.6.20-15-generic/

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1



**I found later that it should be as simple as:**

#install linux-restricted-modules
#go to System -> Administration -> Restricted Drivers Manager and enable the 3945 driver
#command sudo iwconfig eth1 <essid> and sudo iwconfig eth1 key <your_key> (if you use WEP) and sudo dhclient eth1

When I did that it showed the wireless connection first, but then the computer hanged up
I think it happens because I deleted the old ieee80211 files.

May be I am wrong. What can I do now?

Thanks :)

---

