---
title: "still trying to install rt73 0n ubuntu 7.04"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by arielsegal on 2007-08-06
Thanx for the advice from this forum. I still got a problem installing rt73 driver for my usb wifi stick.
I have followed the in struction found at the "HOWTO: RT73 (RT71) serialmonkey drivers" on link [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
It seems that the system detected the old configs. 
I got this message: Update your config and remove /etc/Wireless/RT73STA
How shoul I update the config?
What should I remove? is it the folder RT73STA?
Here are the results:
------------------------------------------------------------------------------------
admin@ariel-desktop:~$ cd /usr/src
admin@ariel-desktop:/usr/src$ sudo cp ~/rt73-cvs-daily.tar.gz /usr/src
Password:
cp: cannot stat `/home/admin/rt73-cvs-daily.tar.gz': No such file or directory
admin@ariel-desktop:/usr/src$ sudo cp '/home/admin/rt73/rt73-cvs-daily.tar.tar'  /usr/src
admin@ariel-desktop:/usr/src$ sudo tar -xvzf rt73-cvs-daily.tar.gz
tar: rt73-cvs-daily.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
admin@ariel-desktop:/usr/src$ ls
linux-headers-2.6.20-15          linux-headers-2.6.20-16-generic
linux-headers-2.6.20-15-generic  rt73-cvs-daily.tar.tar
linux-headers-2.6.20-16
admin@ariel-desktop:/usr/src$ sudo tar -xvzf rt73-cvs-daily.tar.tar
rt73-cvs-2007080502/
rt73-cvs-2007080502/FAQ
rt73-cvs-2007080502/THANKS
rt73-cvs-2007080502/CHANGELOG
rt73-cvs-2007080502/CVS/
rt73-cvs-2007080502/CVS/Root
rt73-cvs-2007080502/CVS/Repository
rt73-cvs-2007080502/CVS/Entries.Log
rt73-cvs-2007080502/CVS/Entries
rt73-cvs-2007080502/LICENSE
rt73-cvs-2007080502/Module/
rt73-cvs-2007080502/Module/auth.c
rt73-cvs-2007080502/Module/rt73.h
rt73-cvs-2007080502/Module/rt73.bin
rt73-cvs-2007080502/Module/rt2x00debug.h
rt73-cvs-2007080502/Module/md5.c
rt73-cvs-2007080502/Module/rtusb_data.c
rt73-cvs-2007080502/Module/rtmp_main.c
rt73-cvs-2007080502/Module/rt_config.h
rt73-cvs-2007080502/Module/assoc.c
rt73-cvs-2007080502/Module/CVS/
rt73-cvs-2007080502/Module/CVS/Root
rt73-cvs-2007080502/Module/CVS/Repository
rt73-cvs-2007080502/Module/CVS/Entries
rt73-cvs-2007080502/Module/wpa.c
rt73-cvs-2007080502/Module/sync.c
rt73-cvs-2007080502/Module/rtmp_info.c
rt73-cvs-2007080502/Module/iwpriv_usage.txt
rt73-cvs-2007080502/Module/rtusb_bulk.c
rt73-cvs-2007080502/Module/mlme.h
rt73-cvs-2007080502/Module/connect.c
rt73-cvs-2007080502/Module/rtmp_tkip.c
rt73-cvs-2007080502/Module/auth_rsp.c
rt73-cvs-2007080502/Module/oid.h
rt73-cvs-2007080502/Module/rtmp_init.c
rt73-cvs-2007080502/Module/TESTING
rt73-cvs-2007080502/Module/rtusb_io.c
rt73-cvs-2007080502/Module/rtmp.h
rt73-cvs-2007080502/Module/mlme.c
rt73-cvs-2007080502/Module/md5.h
rt73-cvs-2007080502/Module/wpa.h
rt73-cvs-2007080502/Module/rtmp_wep.c
rt73-cvs-2007080502/Module/rtmp_def.h
rt73-cvs-2007080502/Module/Makefile
rt73-cvs-2007080502/Module/rtmp_type.h
rt73-cvs-2007080502/Module/sanity.c
rt73-cvs-2007080502/README
admin@ariel-desktop:/usr/src$ sudo aptitude install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
admin@ariel-desktop:/usr/src$ ls
linux-headers-2.6.20-15          linux-headers-2.6.20-16-generic
linux-headers-2.6.20-15-generic  rt73-cvs-2007080502
linux-headers-2.6.20-16          rt73-cvs-daily.tar.tar
admin@ariel-desktop:/usr/src$ cd rt73-cvs-2007080502/Module
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ 
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtmp_init.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/sanity.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtmp_wep.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtmp_info.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/rtmp_tkip.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/wpa.o
  CC [M]  /usr/src/rt73-cvs-2007080502/Module/md5.o
  LD [M]  /usr/src/rt73-cvs-2007080502/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/rt73-cvs-2007080502/Module/rt73.mod.o
  LD [M]  /usr/src/rt73-cvs-2007080502/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 2.7M 2007-08-06 06:06 rt73.ko
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo strip -S rt73.ko
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 243K 2007-08-06 06:07 rt73.ko
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/rt73-cvs-2007080502/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /usr/src/rt73-cvs-2007080502/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
!!!
!!! WARNING: DEPRECATED CONFIG FOUND !
!!!
!!! -> Update your config and remove /etc/Wireless/RT73STA
!!! -> rt73sta.dat file is deprecated: use iwconfig/iwpriv instead
!!! -> rt73.bin firmware has moved to /lib/firmware
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ 
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo modprobe -v rt73
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ lswlan
bash: lswlan: command not found
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ ls /etc/Wireless/RT73STA
rt73.bin  rt73sta.dat
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ ls /etc/Wireless/RT73STA
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ rm /etc/Wireless/RT73STA/rt73sta.dat
rm: remove write-protected regular file `/etc/Wireless/RT73STA/rt73sta.dat'? n
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo rm /etc/Wireless/RT73STA/rt73sta.dat
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo rm /etc/Wireless/RT73STA/rt73.bin
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/rt73-cvs-2007080502/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /usr/src/rt73-cvs-2007080502/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check config ...
!!!
!!! WARNING: DEPRECATED CONFIG FOUND !
!!!
!!! -> Update your config and remove /etc/Wireless/RT73STA
admin@ariel-desktop:/usr/src/rt73-cvs-2007080502/Module$ 
--------------------------------------------------------------------------------------------------------------------------

---

