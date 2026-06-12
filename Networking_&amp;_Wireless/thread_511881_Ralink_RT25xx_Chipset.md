---
title: "Ralink RT25xx Chipset"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by giddy1945 on 2007-07-28
Present circumstances:
No possible wired connection on desktop, I do have Apple laptop w/wireless internet, running 7.04 fresh install with no update on Desktop.  I purchased the Edimax (usb) wireless adapter w/antenna for my desktop (386 system).  The package came with LinuxEmporium's own scrips and directions on a cd.  I followed the directions.  I mounted correctly.  "lspci" does not yield any restults in regards to my adapter. 

Results:  (mixed with commands)

root@ubuntu:/home/tilton# mkdir /root/ralink 
mkdir: cannot create directory `/root/ralink': File exists 
root@ubuntu:/home/tilton# cd /root/ralink 
root@ubuntu:~/ralink# mount 
/dev/sda1 on / type ext3 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
/sys on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
procbususb on /proc/bus/usb type usbfs (rw) 
udev on /dev type tmpfs (rw,mode=0755) 
devshm on /dev/shm type tmpfs (rw) 
devpts on /dev/pts type devpts (rw,gid=5,mode=620) 
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw) 
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=tilton) 
root@ubuntu:~/ralink# tar xvf /media/cdrom0/le_ralink_install.tar 
set_essid.py 
rt73-cvs-2006123101.tar.gz 
rt61-1.1.0-b1.tar.gz 
install_rt61_rt73.sh 
root@ubuntu:~/ralink# ./install_rt61_rt73.sh 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package build-essential 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
linux-headers-2.6.20-15-generic is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Choose Ralink driver to install: 

        1. RT61 - for PCI and PCMCIA cards 
        2. RT73 - for USB dongles 

        Choose 1 or 2 (q quits) 2   

rt73-cvs-2006123101/ 
rt73-cvs-2006123101/CVS/ 
rt73-cvs-2006123101/CVS/Root 
rt73-cvs-2006123101/CVS/Entries.Log 
rt73-cvs-2006123101/CVS/Entries 
rt73-cvs-2006123101/CVS/Repository 
rt73-cvs-2006123101/FAQ 
rt73-cvs-2006123101/LICENSE 
rt73-cvs-2006123101/README 
rt73-cvs-2006123101/TESTING 
rt73-cvs-2006123101/THANKS 
rt73-cvs-2006123101/CHANGELOG 
rt73-cvs-2006123101/Module/ 
rt73-cvs-2006123101/Module/rt_config.h 
rt73-cvs-2006123101/Module/rtmp_main.c 
rt73-cvs-2006123101/Module/rtusb_io.c 
rt73-cvs-2006123101/Module/wpa.h 
rt73-cvs-2006123101/Module/load 
rt73-cvs-2006123101/Module/rtmp_type.h 
rt73-cvs-2006123101/Module/rtmp_tkip.c 
rt73-cvs-2006123101/Module/assoc.c 
rt73-cvs-2006123101/Module/sanity.c 
rt73-cvs-2006123101/Module/oid.h 
rt73-cvs-2006123101/Module/rtmp.h 
rt73-cvs-2006123101/Module/unload 
rt73-cvs-2006123101/Module/iwpriv_usage.txt 
rt73-cvs-2006123101/Module/Makefile 
rt73-cvs-2006123101/Module/rt73.h 
rt73-cvs-2006123101/Module/rtmp_init.c 
rt73-cvs-2006123101/Module/auth_rsp.c 
rt73-cvs-2006123101/Module/rtusb_data.c 
rt73-cvs-2006123101/Module/wpa.c 
rt73-cvs-2006123101/Module/rtmp_info.c 
rt73-cvs-2006123101/Module/sync.c 
rt73-cvs-2006123101/Module/mlme.h 
rt73-cvs-2006123101/Module/rt73.bin 
rt73-cvs-2006123101/Module/rtmp_def.h 
rt73-cvs-2006123101/Module/rt73sta.dat 
rt73-cvs-2006123101/Module/mlme.c 
rt73-cvs-2006123101/Module/rtmp_wep.c 
rt73-cvs-2006123101/Module/ifcfg-rausb0 
rt73-cvs-2006123101/Module/md5.c 
rt73-cvs-2006123101/Module/md5.h 
rt73-cvs-2006123101/Module/connect.c 
rt73-cvs-2006123101/Module/auth.c 
rt73-cvs-2006123101/Module/rtusb_bulk.c 
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic' 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtmp_main.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/mlme.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/connect.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtusb_bulk.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtusb_io.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/sync.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/assoc.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/auth.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/auth_rsp.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtusb_data.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtmp_init.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/sanity.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtmp_wep.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtmp_info.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/rtmp_tkip.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/wpa.o 
  CC [M]  /root/ralink/rt73-cvs-2006123101/Module/md5.o 
  LD [M]  /root/ralink/rt73-cvs-2006123101/Module/rt73.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /root/ralink/rt73-cvs-2006123101/Module/rt73.mod.o 
  LD [M]  /root/ralink/rt73-cvs-2006123101/Module/rt73.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
echo "2.6 module install" 
2.6 module install 
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/root/ralink/rt73-cvs-2006123101/Module  modules_install 
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic' 
  INSTALL /root/ralink/rt73-cvs-2006123101/Module/rt73.ko 
  DEPMOD  2.6.20-15-generic 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
/sbin/depmod -a 
grep: /etc/modprobe.conf: No such file or directory 
append 'alias ra0 rt73' to /etc/modprobe.conf 

Please enter your essid (network id) >> SPRINTNAVYWIFI-40-223 

Please choose encryption type: 

        1. Open - data is not encrypted (insecure!) 
        2. WEP encryption 

        Please choose 1 or 2 (q quits) >> 1 
root@ubuntu:~/ralink# sudo ifup rausb0 
rausb0: ERROR while getting interface flags: No such device 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
rausb0: ERROR while getting interface flags: No such device 
rausb0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up rausb0. 
root@ubuntu:~/ralink# 



                       END



I have looked for informaton regarding my problem for one month.  I just had to finally ask.  Thank you for your help, guys.

---

### Post by kevdog on 2007-07-28
Here's is what I would do -- I would download the serial monkey rt2500 drivers: rt2500 legacy drivers: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

And then use the information in this post as a guide (not a bible) since the guide talks about rt73 -- substitute 2500 for 73 and you should be in business.

About 99% of the info in this post is applicable to you: [http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by giddy1945 on 2007-07-29
Thank you kevdog.  I will do that and poat my results here.  Speaking of results,  My "lspci" did not yeld results, because I have a usb adapter.  "lsusb" told me that it is indeed recognised.  Thanks again.

---

