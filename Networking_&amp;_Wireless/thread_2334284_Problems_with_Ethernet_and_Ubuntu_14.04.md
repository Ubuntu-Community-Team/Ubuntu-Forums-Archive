---
title: "Problems with Ethernet and Ubuntu 14.04"
date: 2016-08-18
forum: Networking &amp; Wireless
---

### Post by KeithSloan on 2016-08-18
My Ethernet keeps dropping its connection.

lspci | grep Ethernet gives

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

lsmod | grep r8 gives
r8169                  77824  0 
mii                    16384  1 r8169

Reading on the net it seems I need to disable the driver r8169 and enable r8168 but when I try and install r8168 with 
apt-get install r8168-dkms I get a crash report error


```
ProblemType: Package
DKMSBuildLog:
 DKMS make.log for r8168-8.037.00 for kernel 3.19.0-65-generic (i686)
 Wed Aug 17 23:10:07 BST 2016
 make: Entering directory `/usr/src/linux-headers-3.19.0-65-generic'
   LD      /var/lib/dkms/r8168/8.037.00/build/built-in.o
   CC [M]  /var/lib/dkms/r8168/8.037.00/build/r8168_n.o
 /var/lib/dkms/r8168/8.037.00/build/r8168_n.c: In function &#8216;rtl8168_init_one&#8217;:
 /var/lib/dkms/r8168/8.037.00/build/r8168_n.c:17103:5: error: implicit declaration of function &#8216;SET_ETHTOOL_OPS&#8217; [-Werror=implicit-function-declaration]
      SET_ETHTOOL_OPS(dev, &rtl8168_ethtool_ops);
      ^
 /var/lib/dkms/r8168/8.037.00/build/r8168_n.c: In function &#8216;rtl8168_schedule_work&#8217;:
 /var/lib/dkms/r8168/8.037.00/build/r8168_n.c:18674:5: error: implicit declaration of function &#8216;PREPARE_DELAYED_WORK&#8217; [-Werror=implicit-function-declaration]
      PREPARE_DELAYED_WORK(&tp->task, task);
      ^
 cc1: some warnings being treated as errors
 make[1]: *** [/var/lib/dkms/r8168/8.037.00/build/r8168_n.o] Error 1
 make: *** [_module_/var/lib/dkms/r8168/8.037.00/build] Error 2
 make: Leaving directory `/usr/src/linux-headers-3.19.0-65-generic'
DKMSKernelVersion: 3.19.0-65-generic

```

Do I have to go back to 12.04. I assume 16.04 will be just as bad if not worse.

---

