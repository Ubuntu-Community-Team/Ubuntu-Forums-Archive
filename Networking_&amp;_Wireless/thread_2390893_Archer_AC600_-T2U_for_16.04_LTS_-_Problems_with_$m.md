---
title: "Archer AC600 -T2U for 16.04 LTS - Problems with $make on kernel 4.13"
date: 2018-05-03
forum: Networking &amp; Wireless
---

### Post by jibbam on 2018-05-03
Hello,

I'm am relatively new to Ubuntu and i am trying to install the driver for my Wifi adapter: AC600-T2U for Ubuntu 16.04 with kernel 4.13.0-39-generic. I have a dual boot with Windows 10 on my laptop. I followed procedures from the following link:

_[http://samliu.github.io/2016/10/09/tplink-archer-t2uh.html](http://samliu.github.io/2016/10/09/tplink-archer-t2uh.html)_

However when I try to use "make" to install the driver I get the following error:

jip@JipPC:~/src/mt7610u_wifi_sta_v3002_dpo_20130916$ make
make -C tools
make[1]: Entering directory '/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/tools'
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/tools/bin2h
chipset = mt7610u
chipset = mt7650u
cp -f os/linux/Makefile.6 /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/Makefile
make -C /lib/modules/4.13.0-39-generic/build SUBDIRS=/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-39-generic'
  CC [M]  /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o
In file included from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44:0,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rt_config.h:33,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:28:
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:77:0: warning: "EXT_BUILD_CHANNEL_LIST" redefined
 #define EXT_BUILD_CHANNEL_LIST  /* must define with CRDA */
 ^
<command-line>:0:0: note: this is the location of the previous definition
In file included from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:98:0,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rt_config.h:33,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:28:
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/cfg80211.h:35:49: error: ‘IEEE80211_NUM_BANDS’ undeclared here (not in a function)
  struct ieee80211_supported_band Cfg80211_bands[IEEE80211_NUM_BANDS];
                                                 ^
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c: In function ‘announce_802_3_packet’:
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:341:16: warning: unused variable ‘pAd’ [-Wunused-variable]
  RTMP_ADAPTER *pAd = (RTMP_ADAPTER *)pAdSrc;
                ^
In file included from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44:0,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/rt_config.h:33,
                 from /home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:28:
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:450:35: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
                                   ^
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:669:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:450:9: note: in expansion of macro ‘DBGPRINT’
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
         ^
scripts/Makefile.build:316: recipe for target '/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o' failed
make[2]: *** [/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o] Error 1
Makefile:1550: recipe for target '_module_/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux' failed
make[1]: *** [_module_/home/jip/src/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-39-generic'
Makefile:403: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2



I tried my best but i have no idea how to solve this.  The driver that was referred to in the previous given link at the bottom gives me the same problem (_[https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916](https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916)_).

Any advice? I have been struggling for a few days now unfortunately.

Kind regards,

Jip

---

### Post by chili555 on 2018-05-03
This will never ever ever never ever work. Please see my post #18 here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u)

> There is little to nothing we can do when MediaTek and TP-Link don't supply a driver for newer kernels; i.e. 4.8 and newer.Sorry.

---

### Post by jibbam on 2018-05-05
Ok that is a clear (although unfortunate) answer. Seems like I will be buying another USB device that is supported then. Thanks for the help! Any suggestions btw?

---

### Post by chili555 on 2018-05-05
Please see my post #22 here: [https://ubuntuforums.org/showthread.php?t=2359573](https://ubuntuforums.org/showthread.php?t=2359573)

---

### Post by jibbam on 2018-05-23
Thanks again chili555 for your help. I bought the unit installed the correct driver and things are working great now. Cheers!

---

### Post by m3318 on 2018-11-08
try this its successfully worked in linux mint 19 cinnamon (kernel version 4.15.0-20-generic)
[https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes)
Building
    1  sudo apt-get install linux-headers-$(uname -r)
    2  sudo apt-get install gcc
    3  sudo apt-get install update
    4  sudo apt-get install linux-source
    5  sudo apt-get install linux-headers-$(uname -r)
    6  sudo apt-get install build-essential
    7  cd mt7610u-linksys-ae6000-wifi-fixes-master
    8  sudo make clean
    9  sudo make
    10 sudo make install

Building with DKMS

   11  sudo apt-get install dkms
   12  sudo cp -R . /usr/src/mt7610u_sta-1.0
   13  sudo dkms add mt7610u_sta/1.0
   14  sudo dkms build mt7610u_sta/1.0
   15  sudo dkms install mt7610u_sta/1.0
   16  reboot

---

### Post by alathen on 2018-12-05
I can confirm that the driver listed above by m3318:
[https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes)
works for kubuntu 16.04.05 with kernel 4.15.
I used Archer AC600 T2U. I also tried 2 or 3 other drivers from github for chipset MT7610U but only this one seems to compile and work for me without completely freezing my pc. 

Thank you m3318 for your post, I thought there was no hope left to get this working.

---

### Post by triedallthetimeandfailed on 2019-01-06
thank you. worked.

---

### Post by jankempeneers on 2019-07-15
Worked like a charm on Ubuntu 16.04, Thx!

---

