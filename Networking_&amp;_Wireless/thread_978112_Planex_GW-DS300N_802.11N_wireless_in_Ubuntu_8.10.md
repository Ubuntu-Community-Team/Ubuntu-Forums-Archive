---
title: "Planex GW-DS300N 802.11N wireless in Ubuntu 8.10"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Steve1496 on 2008-11-10
I have a [Planex GW-DS300N]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833360012&Tpk=33-360-012") installed in my system and can't figure out how to get it to work.  The card shows up as a Ralink RT2800 model in Ubuntu.  I could not install the drivers as per the instructions [here]("http://ubuntuforums.org/showthread.php?t=844599") for the 2860, because when I try to do the make command, it returns the following:
```
root@ubuntu:/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0# make
make -C tools
make[1]: Entering directory `/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o
/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt_ieee80211_if_setup’:
/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c:672: error: ‘struct net_device’ has no member named ‘nd_net’
make[2]: *** [/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o] Error 1
make[1]: *** [_module_/home/steve/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [LINUX] Error 2
```

I've tried ndiswrapper with a no go.  I'm currently using an Ethernet bridge that I use with my TiVo, so I would like to square away the wireless problem.  Any and all help is greatly appreciated!

Steve

---

### Post by Steve1496 on 2008-11-11
Any ideas how to fix this Error 2 problem when trying to do make on the RT2860 drivers in 8.10 Kernel 2.6.27-7?  I do have build-essentials and linux-headers-generic installed.

---

### Post by eldiabolosk on 2008-11-23
I have an SMCWPCI-N2 with the same chip RT2800 RaLink. Did you find out how to get your card to work?

(To find out more about hardware in terminal run "lspci").

Ed.

---

### Post by eldiabolosk on 2009-06-11
I recently installed Ubuntu 9.04 (Jaunty). This card worked out if box for me. It was a fresh install. Maybe I was lucky, but it worked for me.

---

