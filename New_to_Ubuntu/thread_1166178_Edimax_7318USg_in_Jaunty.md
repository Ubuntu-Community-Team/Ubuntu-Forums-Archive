---
title: "Edimax 7318USg in Jaunty"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Noob McClendon on 2009-05-21
Can one of you kind souls help me out?

I just installed the Jaunty release candidate on a fresh hard drive and I need to get the Edimax 7318USg([http://www.edimax.com/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44#03](http://www.edimax.com/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44#03)) to work on it.  I went to the Edimax site and downloaded their Linux source code (RT73 driver), but when I try to build the driver, I get the following output:

tenshin@tenshin:~/RT73_Linux_STA_Drv1.1.0.0/Module$ make all
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘usb_rtusb_close_device’:
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:434: error: implicit declaration of function ‘kill_proc’
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1133: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1154: error: ‘struct net_device’ has no member named ‘weight’
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1181: warning: passing argument 1 of ‘dev_get_by_name’ from incompatible pointer type
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1181: error: too few arguments to function ‘dev_get_by_name’
make[2]: *** [/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

I've read a couple of other threads where people have seemed to have been able to install this configuration without running into this problem. So I don't know what I'm doing wrong.  Any help would be much appreciated.

---

### Post by Talon2 on 2009-05-21
> **Noob McClendon said:**
> Can one of you kind souls help me out?

I just installed the Jaunty release candidate on a fresh hard drive and I need to get the Edimax 7318USg([http://www.edimax.com/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44#03](http://www.edimax.com/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44#03)) to work on it.  I went to the Edimax site and downloaded their Linux source code (RT73 driver), but when I try to build the driver, I get the following output:

tenshin@tenshin:~/RT73_Linux_STA_Drv1.1.0.0/Module$ make all
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘usb_rtusb_close_device’:
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:434: error: implicit declaration of function ‘kill_proc’
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1133: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1154: error: ‘struct net_device’ has no member named ‘weight’
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1181: warning: passing argument 1 of ‘dev_get_by_name’ from incompatible pointer type
/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:1181: error: too few arguments to function ‘dev_get_by_name’
make[2]: *** [/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/tenshin/RT73_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

I've read a couple of other threads where people have seemed to have been able to install this configuration without running into this problem. So I don't know what I'm doing wrong.  Any help would be much appreciated.

That device should be supported without the need to do anything other than start the Network Manager applet so as to select an AP.

Why do you think it is not working?

---

