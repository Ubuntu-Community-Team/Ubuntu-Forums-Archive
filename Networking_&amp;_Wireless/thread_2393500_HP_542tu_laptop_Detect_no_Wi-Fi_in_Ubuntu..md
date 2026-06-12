---
title: "HP 542tu laptop Detect no Wi-Fi in Ubuntu."
date: 2018-06-04
forum: Networking &amp; Wireless
---

### Post by jaseemharry on 2018-06-04
I am duel booting Ubuntu 14.04 with windows 10. In windows 10 Wi-Fi works fine. But in ubuntu i can't Even detect Wi-Fi. 
I searched around a little and found out This. [https://github.com/jeremyb31/rtl8723de](https://github.com/jeremyb31/rtl8723de)
But i get the following error.


```
$ sudo dkms add ./rtl8723de

Creating symlink /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/source ->
                 /usr/src/rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414

DKMS: add completed.
$ sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' all KVER=4.11.12-041112-generic...........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8723de: 5.1.1.8_21285.20171026_COEX20170111-1414 not found
Error! Bad return status for module build on kernel: 4.11.12-041112-generic (x86_64)
Consult /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log for more information.

$ cat /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log

DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 4.11.12-041112-generic (x86_64)
Mon Jun  4 22:23:07 IST 2018
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.11.12-041112-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build  modules
make[1]: Entering directory `/usr/src/linux-headers-4.11.12-041112-generic'
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mi.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/pci_intf.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/pci_ops_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.o
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_indicate_connect’:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:744:10: error: variable ‘roam_info’ has initializer but incomplete type
   struct cfg80211_roam_info roam_info = {};
          ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:744:29: error: storage size of ‘roam_info’ isn’t known
   struct cfg80211_roam_info roam_info = {};
                             ^
In file included from ./include/linux/kmod.h:22:0,
                 from ./include/linux/module.h:13,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/basic_types.h:81,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:31,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/linux/gfp.h:239:20: warning: passing argument 3 of ‘cfg80211_roamed’ makes pointer from integer without a cast [-Wint-conversion]
 #define GFP_ATOMIC (__GFP_HIGH|__GFP_ATOMIC|__GFP_KSWAPD_RECLAIM)
                    ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:760:50: note: in expansion of macro ‘GFP_ATOMIC’
   cfg80211_roamed(padapter->pnetdev, &roam_info, GFP_ATOMIC);
                                                  ^
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:91:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/net/cfg80211.h:5233:6: note: expected ‘const u8 * {aka const unsigned char *}’ but argument is of type ‘unsigned int’
 void cfg80211_roamed(struct net_device *dev,
      ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:760:3: error: too few arguments to function ‘cfg80211_roamed’
   cfg80211_roamed(padapter->pnetdev, &roam_info, GFP_ATOMIC);
   ^
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:91:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/net/cfg80211.h:5233:6: note: declared here
 void cfg80211_roamed(struct net_device *dev,
      ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_preinit_wiphy’:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6762:7: error: ‘struct wiphy’ has no member named ‘max_sched_scan_reqs’
  wiphy->max_sched_scan_reqs = 1;
       ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c: At top level:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6795:25: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .change_virtual_intf = cfg80211_rtw_change_iface,
                         ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6795:25: note: (near initialization for ‘rtw_cfg80211_ops.change_virtual_intf’)
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6818:22: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .add_virtual_intf = cfg80211_rtw_add_virtual_intf,
                      ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6818:22: note: (near initialization for ‘rtw_cfg80211_ops.add_virtual_intf’)
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.11.12-041112-generic'
make: *** [modules] Error 2
```



Please help. I don't know what to do now. I just want to connect my laptop to Wi-Fi.

---

### Post by jeremy31 on 2018-06-04
What git clone command did you run```
 history | grep clone
```
You should stick with the 4.4 kernels rather than 4.11

---

### Post by jaseemharry on 2018-06-04
Thanks for the reply.
I Tried [https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-amp-Bluetooth-Linux-driver/m-p/6477307/highlight/true#M146067](https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-amp-Bluetooth-Linux-driver/m-p/6477307/highlight/true#M146067) and it worked. I can use Wi-Fi now on my laptop now.
[PS:I tried "[COLOR=#24292E][FONT=-apple-system]git clone [/FONT][/COLOR][https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)" (My kernel is 4.11.12) in my first try]

---

