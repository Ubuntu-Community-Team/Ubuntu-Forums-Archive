---
title: "linux-wlan-ng-0.2.3 patching and compileing problems"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Darth_tater on 2006-11-16
Hello!

long time SUSE user, thought id give ubuntu a try.

lets just say that, they both have their strengths.

my only two MAJOR problems are that my screen resolution cant go higher than 1024 * 768 (its a 21 inch CRT and i have a 7800GT, yes i go the Nvidia driver working)

and my more important problem.

i have a prism 2 USB dongle and i found out how to get the linux-wlan-ng drivers working flawlessly using the built-in repo drivers... however, those don't work with packet injection :(

so i found all that i need to do to get the drivers and the patch, but compileing them gives me errors.

here is what i am doing 

```

wget ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/linux-wlan-ng-0.2.3.tar.gz
wget http://patches.aircrack-ng.org/linux-wlan-0.2.3.packet.injection.patch
tar -xvzf wlanng-0.2.3.tar.gz
cd linux-wlan-ng-0.2.3
patch -Np1 -i ../linux-wlan-0.2.3.packet.injection.patch
```

the i run "make config && make all && make install"

which spits out the following:

```
karl@x64:~/linux-wlan-ng-0.2.3$ sudo make config && make all && make install
Password:

-------------- Linux WLAN Configuration Script -------------

The default responses are correct for most users.

Build Prism2.x PCMCIA Card Services (_cs) driver? (y/n) [n]: n
Build Prism2 PLX9052 based PCI (_plx) adapter driver? (y/n) [n]: n
Build Prism2.5 native PCI (_pci) driver? (y/n) [n]: n
Build Prism2.5 USB (_usb) driver? (y/n) [y]: y

Linux source directory [/lib/modules/2.6.17-10-386/build]:

The kernel source tree is version 2.6.17-10-386.
Kernel 2.5/2.6 support is highly experimental.

The current kernel build date is Fri Oct 13 18:41:40 2006.

Alternate target install root directory on host []:   Module install directory [/lib/modules/2.6.17-10-386]:

It looks like you have a System V init file setup.


Prefix for build host compiler? (rarely needed) []:

Build for debugging (see doc/config.debug) (y/n) [n]:


Configuration successful.  Now type 'make' and pray.

set -e; for d in src doc man etc; do make -C $d ; done
make[1]: Entering directory `/home/karl/linux-wlan-ng-0.2.3/src'
set -e; for d in mkmeta p80211 prism2 shared wlanctl wland nwepgen wlancfg; do make WLAN_SRC=/home/karl/linux-wlan-ng-0.2.3/src/ -C $d ; done
make[2]: Entering directory `/home/karl/linux-wlan-ng-0.2.3/src/mkmeta'
gcc -E -M -I../include -I/lib/modules/2.6.17-10-386/build/include -D__LINUX_WLAN__ ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetadef.c ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetastruct.c > .depend
make[2]: Leaving directory `/home/karl/linux-wlan-ng-0.2.3/src/mkmeta'
make[2]: Entering directory `/home/karl/linux-wlan-ng-0.2.3/src/mkmeta'
mkdir -p obj
make[2]: Leaving directory `/home/karl/linux-wlan-ng-0.2.3/src/mkmeta'
make[2]: Entering directory `/home/karl/linux-wlan-ng-0.2.3/src/p80211'
make -C /lib/modules/2.6.17-10-386/build M='/home/karl/linux-wlan-ng-0.2.3/src/p80211/.. /home/karl/linux-wlan-ng-0.2.3/src/p80211' WLAN_SRC=/home/karl/linux-wlan-ng-0.2.3/src/ modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  Building modules, stage 2.
  MODPOST
/home/karl/linux-wlan-ng-0.2.3/src/p80211/Modules.symvers: No such file or directory
Aborted
make[4]: *** [__modpost] Error 134
make[3]: *** [modules] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/home/karl/linux-wlan-ng-0.2.3/src/p80211'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/karl/linux-wlan-ng-0.2.3/src'
make: *** [all] Error 2

```

any help you can provide would be greatly appreciated.  THANKS!

---

### Post by ghettobilly on 2006-11-18
get module-assistant and wlan-ng-source from apt
go to /usr/src extract linux-wlan-ng.tar.gz it creates folder /usr/src/modules/linux-wlan-ng
run the patch in /usr/src/modules
delete the linux-wlan-ng.tar.gz (so module-assistant doesnt overwrite your patched version)
run module-assistant go to select > wlan-ng > ok > build when it ask to download source select no after it builds it ask to install new modules
you now have patched wlan-ng

---

### Post by Darth_tater on 2006-11-18
thanks so much.

im in vita right now (i test and boot lots of Os's)but ill give this a try ASAP and post back if i had any problems.

again, i appreciate your helping me out.

---

