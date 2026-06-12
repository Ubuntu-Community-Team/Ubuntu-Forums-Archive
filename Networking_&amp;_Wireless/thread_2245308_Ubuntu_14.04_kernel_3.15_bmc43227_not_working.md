---
title: "Ubuntu 14.04 kernel 3.15 bmc43227 not working"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by cmoud94 on 2014-09-22
Hi everyone,

I have a kernel 3.15.0 installed and I can't get my BCM43227 wireless card working. I've used it before with the same kernel etc. But after system reinstall it's not working. Before I've found a tutorial how to patch the bcmwl source for the kernel 3.15 and up. Now... I can't find it anymore.

Here is the build log:
> DKMS make.log for bcmwl-6.30.223.141+bdcom for kernel 3.15.0-031500-generic (x86_64)
Mon Sep 22 21:58:06 CEST 2014
make: Entering directory `/usr/src/linux-headers-3.15.0-031500-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function ‘wl_notify_connect_status’:
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1844:4: warning: passing argument 3 of ‘cfg80211_ibss_joined’ makes pointer from integer without a cast [enabled by default]
    cfg80211_ibss_joined(ndev, (u8 *)&wl->bssid, GFP_KERNEL);
    ^
In file included from /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:33:0:
include/net/cfg80211.h:3933:6: note: expected ‘struct ieee80211_channel *’ but argument is of type ‘unsigned int’
 void cfg80211_ibss_joined(struct net_device *dev, const u8 *bssid,
      ^
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1844:4: error: too few arguments to function ‘cfg80211_ibss_joined’
    cfg80211_ibss_joined(ndev, (u8 *)&wl->bssid, GFP_KERNEL);
    ^
In file included from /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:33:0:
include/net/cfg80211.h:3933:6: note: declared here
 void cfg80211_ibss_joined(struct net_device *dev, const u8 *bssid,
      ^
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.15.0-031500-generic'



I know that the problem is in the **cfg80211_ibss_joined()** function, but I don't remember how to fix it and ho to rebuild the source code to complete the bcmwl installation.

Thanks for help, Marek.

---

### Post by praseodym on 2014-09-22
Try the driver version 6.30.223.248 from 14.10:

[http://packages.ubuntu.com/utopic/bcmwl-kernel-source](http://packages.ubuntu.com/utopic/bcmwl-kernel-source)

---

### Post by cmoud94 on 2014-09-23
Is there a precompiled *.deb of this version? I get this errors when I'm trying to compile it.
> cmoud94@Anonymous ~/Desktop/bcmwl-6.30.223.248+bdcom $ sudo make clean
[sudo] password for cmoud94: 
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-3.15.0-031500-generic'
CFG80211 API is prefered for this kernel version
/home/cmoud94/Desktop/bcmwl-6.30.223.248+bdcom/Makefile:85: Neither CFG80211 nor Wireless Extension is enabled in kernel
make[1]: Leaving directory `/usr/src/linux-headers-3.15.0-031500-generic'
cmoud94@Anonymous ~/Desktop/bcmwl-6.30.223.248+bdcom $ sudo make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.15.0-031500-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /home/cmoud94/Desktop/bcmwl-6.30.223.248+bdcom/built-in.o
make[2]:  *** No rule to make target  `/home/cmoud94/Desktop/bcmwl-6.30.223.248+bdcom/src/shared/linux_osl.o',  needed by `/home/cmoud94/Desktop/bcmwl-6.30.223.248+bdcom/wl.o'.  Stop.
make[1]: *** [_module_/home/cmoud94/Desktop/bcmwl-6.30.223.248+bdcom] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.15.0-031500-generic'
make: *** [all] Error 2
cmoud94@Anonymous ~/Desktop/bcmwl-6.30.223.248+bdcom $ 


---

### Post by praseodym on 2014-09-23
Scroll down that link and click on "i386" for 32 bit or "amd64" for 64bit.

---

### Post by cmoud94 on 2014-09-23
Thanks so much. It works now! :)

---

### Post by mbeach on 2014-10-25
thank you. saved me some aggravation.

---

