---
title: "Realtek's RTL8185 and ubuntu 8.04?"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by PBK on 2008-04-28
Hello,

  I have a Gateway MX3414 with a realtek rtl8185 wireless chip. Wireless setup worked in 7.10 without encryption using a r8180 module. lspci in 8.04 shows that the system acknowledges the wireless chip, but no module loaded nor can I get one to compile. Fresh install, BTW.

  Has any been able to get a similar setup to work under 8.04? What can I do?

  Thank you...

Paul

---

### Post by chili555 on 2008-04-28
May we please see:```
sudo modprobe r8180
sudo lshw -C network
```> nor can I get one to compileHow so? If the tarball (the *.tar.gz file) is pretty current, it can probably can be tweaked and compiled.

---

### Post by chili555 on 2008-04-28
You might also check here: [http://ubuntuforums.org/showthread.php?t=772006](http://ubuntuforums.org/showthread.php?t=772006)

---

### Post by PBK on 2008-04-28
Here is what I got:

sudo modprobe r8180:

FATAL: Module r8180 not found.



sudo lshw -C network:

  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32



When I run ./makedrv, I get:

ieee80211/
ieee80211/ieee80211_tx.c
ieee80211/Modules.symvers
ieee80211/ieee80211_softmac_wx.c
ieee80211/LICENSE
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_module.c
ieee80211/Makefile
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_softmac.c
ieee80211/README
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_crypt.c
rtl818x-0.1/
rtl818x-0.1/r8180_wx.h
rtl818x-0.1/r8180_wx.c
rtl818x-0.1/r8180_rtl8225.h
rtl818x-0.1/r8180_rtl8255.h
rtl818x-0.1/AUTHORS
rtl818x-0.1/r8180_max2820.c
rtl818x-0.1/r8180.h
rtl818x-0.1/r8180_max2820.h
rtl818x-0.1/tags
rtl818x-0.1/r8180_sa2400.h
rtl818x-0.1/r8180_93cx6.c
rtl818x-0.1/ieee80211.h
rtl818x-0.1/r8180_gct.c
rtl818x-0.1/r8180_gct.h
rtl818x-0.1/.r8180_core.o.d
rtl818x-0.1/r8180_rtl8225.c.old
rtl818x-0.1/Modules.symvers
rtl818x-0.1/CHANGES
rtl818x-0.1/LICENSE
rtl818x-0.1/r8180_93cx6.h
rtl818x-0.1/README.master
rtl818x-0.1/r8180_hw.h
rtl818x-0.1/README
rtl818x-0.1/r8180_pm.c
rtl818x-0.1/r8180_sa2400.c
rtl818x-0.1/COPYING
rtl818x-0.1/README.adhoc
rtl818x-0.1/r8180_rtl8225.c
rtl818x-0.1/.tmp_versions/
rtl818x-0.1/.tmp_versions/r8180.mod
rtl818x-0.1/INSTALL
rtl818x-0.1/r8180_rtl8255.c
rtl818x-0.1/r8180_core.c
rtl818x-0.1/r8180_pm.h
rtl818x-0.1/Makefile
rtl818x-0.1/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /rtl8185_linux_26.1010.0531.2006/ieee80211/tmp
make -C /lib/modules/2.6.24-16-generic/build M=/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_stop_scan’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_abort’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_stop_protocol’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2059: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: ‘INIT_WORK’ undeclared (first use in this function)
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: (Each undeclared identifier is reported only once
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: for each function it appears in.)
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2168:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2169:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2170:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2171:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_free’:
/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2191: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
make[2]: *** [/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/rtl8185_linux_26.1010.0531.2006/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp
make -C /lib/modules/2.6.24-16-generic/build M=/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o
In file included from /rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:61:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.h:29:26: error: linux/config.h: No such file or directory
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_proc_module_init’:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:541: error: ‘proc_net’ undeclared (first use in this function)
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:541: error: (Each undeclared identifier is reported only once
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:541: error: for each function it appears in.)
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_proc_module_remove’:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:547: error: ‘proc_net’ undeclared (first use in this function)
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_rx’:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2080: error: implicit declaration of function ‘rdtsc’
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_init’:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: ‘INIT_WORK’ undeclared (first use in this function)
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_pci_probe’:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3960: error: implicit declaration of function ‘SET_MODULE_OWNER’
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4031: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_pci_module_init’:
/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4156: error: implicit declaration of function ‘pci_module_init’
make[2]: *** [/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o] Error 1
make[1]: *** [_module_/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2




  Thanks for any direction you can point me in!

Paul

---

### Post by chili555 on 2008-04-29
Wow! That's quite a mess. Even though I consider myself a pretty fair compiler, I had a mess, too.

I found this: [http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems](http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems)  I downloaded his patched driver and got it to ./makedrv with warnings but no errors. Please try it and let us know.

---

