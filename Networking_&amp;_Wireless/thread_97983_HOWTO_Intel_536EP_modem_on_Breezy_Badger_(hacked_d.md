---
title: "HOWTO: Intel 536EP modem on Breezy Badger (hacked driver)"
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by _Ramirez_ on 2005-12-02
(HACKED DRIVER) Finally working so here is the howto:

[LIST=1]
[*] Download 4.71 driver from Intel's website:

[INDENT][ftp://aiedownload.intel.com/df-support/9266/eng/Intel-536EP-4.71.tgz](ftp://aiedownload.intel.com/df-support/9266/eng/Intel-536EP-4.71.tgz)
(if this link doesn't work then find the driver on website, it's easy)[/INDENT]


[*] Change the Intel536_inst file with the one I uploaded with this message.


[*] **sudo apt-get install make m4 gcc-3.4 g++ automake autoconf**


[*] from synaptic add more packages (it's easier to find them this way)

[INDENT]your keywords are linux, kernel, image, source, headers
find these packages and install them, I don't know their names but you won't 
have any problems if you add them all... everything that's got to do with kernel source[/INDENT]


[*] cd yourself to Intel-536 dir you unpacked earlier from downloaded .tgz and run:

[INDENT][B]sudo make clean
sudo make 536
sudo make install[/B]
[/INDENT]

this should install your driver, but for me it only worked using vwdialconf. 
[/LIST]


I didn't want to spend all day configuring so I installed gnome-ppp:

[LIST=1]
[*] Downloaded source from:

[INDENT][http://www.gnome-ppp.org/download/0.3/gnome-ppp-0.3.21.tar.gz](http://www.gnome-ppp.org/download/0.3/gnome-ppp-0.3.21.tar.gz)
this address will probably change in future!!![/INDENT]

[*] **sudo apt-get install libgnomeui-dev intltool**


[*] cd yourself into gnome-ppp dir and run:

[INDENT][B]sudo ./configure --prefix=/usr
sudo make
sudo make install[/B]
[/INDENT]

[*] now you have gnome-ppp icon in your internet application group
[/LIST]

NOTE: you must run gnome-ppp as root, so I did this:
	**How to use "sudo" without prompt for password (not secure)?**
from ubuntuguide and than added the sudo prefix in the "command" section of gnome-ppp shortcut. Maybe there is some other way to do this?

**This HOWTO wouldn't be possible without my good friend vladeck, the author of gnome-ppp. Thanks again!**

---

### Post by diablo_ on 2005-12-08
I can't find out whats wrong?!

drtwdiablo@Ubuntu:~/Desktop/Intel-536$ sudo apt-get install make m4 gcc-3.4 g++ automake autoconf
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

SECOND ERROR!

drtwdiablo@Ubuntu:~/Desktop/Intel-536$ sudo make 536 Try `uname --help' for more information.
   Module precompile check
   Current running kernel is: 2.6.12-9-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
cd coredrv && make 536core_26 && \
cp Intel536.ko .. && cd .. && \
strip --strip-debug Intel536.ko && \
exit; \
ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
if [  ]; then \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
else \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
cp Intel536.o .. ; \
if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.12-9-386
make[1]: Entering directory `/home/drtwdiablo/Desktop/Intel-536/coredrv'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/drtwdiablo/Desktop/Intel-536/coredrv modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/drtwdiablo/Desktop/Intel-536/coredrv/coredrv.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/drtwdiablo/Desktop/Intel-536/coredrv/coredrv.o] Error 127
make[2]: *** [_module_/home/drtwdiablo/Desktop/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/drtwdiablo/Desktop/Intel-536/coredrv'
2.6.12-9-386
Failed to build driver

---

### Post by _Ramirez_ on 2005-12-09
Your package database is locked because it's used by another process? Try restarting and than adding those packages from synaptic, but be sure to run synaptic before anything else. Second error will disapear when you install required packages, you can't build driver without them!

---

### Post by njmf on 2005-12-22
If you want to allow any user to dial from gppp, just allow them to write to modem device (/dev/536ep in this case).
Besides doing what _Ramirez_ told you there, you need to open file Intel536_boot, find these lines near the begining of the file:
serial="Intel536"
devnode="/dev/536ep"
device="536ep"
registry="hamregistry"
group="root"
mode="664"
--
and change
*mode="664"* to
*mode="666"*
and then install it the way _Ramirez_ told. If you already have installed driver, uninstall it with command:
*sudo make uninstall*
and then install it again with these modifications.

It now creates (at boot time) modem device with rw access for all.
Hope it helped, and thanks _Ramirez_ for doing inst hack, it was realy helpful! ;)

---

