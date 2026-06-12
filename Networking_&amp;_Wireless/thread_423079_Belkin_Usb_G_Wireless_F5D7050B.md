---
title: "Belkin Usb G Wireless F5D7050B"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by godx3 on 2007-04-25
So... I've followed a lot of tutorials, but i wasn't be able to check out this problem!
I've installed Ubuntu 7.04 Feisty Fawn - linux 2.6.20-15
The belkin usb adapter isn't working! If I connect it to the usb port, everything slow down! Even if i unconnect it! In these cases I'm obliged to reboot
I really doesn't know how to do it...
Now I'm going to write every information about the dispositive:
Belkin Wireless G (802.11g) USB Network Adapter
IC ID: 3623A-F5D7050B
FCC ID: K7S-F5D7050B
On the box there's a label on which is written "version 3000ef"

Following this tutorial 
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)) 
during the making step, I noticed these errors in the terminal:

> godx3@godx3-desktop:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65: error: stray ‘\303’ in program
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65: error: stray ‘\227’ in program
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65:42: error: invalid suffix "d" on integer constant
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65: error: expected ‘)’ before numeric constant
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65: error: stray ‘\303’ in program
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65: error: stray ‘\227’ in program
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65:42: error: invalid suffix "a" on integer constant
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:65: error: expected ‘)’ before numeric constant
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/godx3/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 

Is there any solution to this problem? Thx to all...

---

### Post by SnoutUK on 2007-04-25
I use the exact same thing here, but i cant see that i have that problem! Due to my very slight experience with ubuntu i can only suggest you do the install again from scratch

---

### Post by Scalesin on 2008-02-07
Hi there,
This is a good HOWTO. 

[http://www.linuxforums.org/forum/wireless-internet/87162-belkin-802-11g-wireless-g-usb-network-adapter-problem-4.html](http://www.linuxforums.org/forum/wireless-internet/87162-belkin-802-11g-wireless-g-usb-network-adapter-problem-4.html)

**_Appendix:[_**

- install ndiswrapper
- Start terminal
  Type:   vim /etc/modprobe.d/blacklist
            blacklist rt73usb
            blacklist rt2570
            blacklist rt2500usb


  Download the windows driver rt73 version 3 from Belkin.

  [http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221)
   or
[http://www.belkin.com/support/article/?lid=en&pid=f5d7050&aid=5381&scid=221&fid=2395&fn=f5d7050v3.exe](http://www.belkin.com/support/article/?lid=en&pid=f5d7050&aid=5381&scid=221&fid=2395&fn=f5d7050v3.exe)

   Unpack the exe-file 

Follow the HOWTO


Is working...:-D

Good Luck !

Sincerely Yours

Scalesin

---

