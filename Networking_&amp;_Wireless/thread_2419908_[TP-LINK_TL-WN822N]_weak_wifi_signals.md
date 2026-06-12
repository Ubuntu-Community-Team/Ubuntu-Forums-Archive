---
title: "[TP-LINK TL-WN822N] weak wifi signals"
date: 2019-05-27
forum: Networking &amp; Wireless
---

### Post by razorrzr0 on 2019-05-27
I am facing a issue of weak wifi signals.
i tried installing alternative driver but i facing this issue
```
sudo dkms install rtl8192eu/1.0

Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...
'make' all KVER=5.0.0-15-generic........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8192eu: 1.0 not found
Error! Bad return status for module build on kernel: 5.0.0-15-generic (x86_64)
Consult /var/lib/dkms/rtl8192eu/1.0/build/make.log for more information.
```
and here's the make.log
```
DKMS make.log for rtl8192eu-1.0 for kernel 5.0.0-15-generic (x86_64)Mon May 27 12:47:44 IST 2019
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.0.0-15-generic/build M=/var/lib/dkms/rtl8192eu/1.0/build  modules
make[1]: Entering directory '/usr/src/linux-headers-5.0.0-15-generic'
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_cmd.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_cmd.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_cmd.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c: In function &#8216;aes_cipher&#8217;:
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c:1598:5: warning: this &#8216;for&#8217; clause does not guard... [-Wmisleading-indentation]
     for (j = 0; j < 8; j++)
     ^~~
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c:1601:2: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;for&#8217;
  payload_index = hdrlen + 8;
  ^~~~~~~~~~~~~
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c: In function &#8216;aes_decipher&#8217;:
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c:1984:5: warning: this &#8216;for&#8217; clause does not guard... [-Wmisleading-indentation]
     for (j = 0; j < 8; j++)
     ^~~
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_security.c:1987:2: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;for&#8217;
  payload_index = hdrlen + 8;
  ^~~~~~~~~~~~~
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_debug.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_debug.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_debug.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_io.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_io.c:52:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_io.c:52:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ioctl_query.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ioctl_query.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ioctl_query.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ioctl_set.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ioctl_set.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ioctl_set.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ieee80211.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ieee80211.c:25:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ieee80211.c:25:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/../hal/phydm/phydm_types.h:176,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/../hal/phydm/phydm_precomp.h:24,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/hal_data.h:25,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/../hal/phydm/phydm_types.h:176,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/../hal/phydm/phydm_precomp.h:24,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/hal_data.h:25,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c: In function &#8216;rtw_delba_check&#8217;:
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c:12427:7: warning: this &#8216;else&#8217; clause does not guard... [-Wmisleading-indentation]
       else
       ^~~~
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c:12429:8: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;else&#8217;
        psta->recvreorder_ctrl[i].enable = _FALSE;
        ^~~~
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c:12430:7: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
       if (ret != _FAIL)
       ^~
/var/lib/dkms/rtl8192eu/1.0/build/core/rtw_mlme_ext.c:12432:8: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;if&#8217;
        rtw_reset_continual_no_rx_packet(psta, i);
        ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_wlan_util.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_wlan_util.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_wlan_util.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_vht.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_vht.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_vht.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_pwrctrl.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_pwrctrl.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_pwrctrl.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_rf.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_rf.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_rf.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_recv.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_recv.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_recv.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_sta_mgt.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_sta_mgt.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_sta_mgt.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ap.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ap.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_ap.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_xmit.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_xmit.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_xmit.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_p2p.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_p2p.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_p2p.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_tdls.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_tdls.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_tdls.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_br_ext.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_br_ext.c:32:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_br_ext.c:32:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_iol.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_iol.c:21:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_iol.c:21:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_sreset.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_sreset.c:21:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_sreset.c:21:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_beamforming.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_beamforming.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_beamforming.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_odm.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/rtw_odm.h:23,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_odm.c:21:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/rtw_odm.h:23,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/rtw_odm.c:21:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/core/efuse/rtw_efuse.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/efuse/rtw_efuse.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/core/efuse/rtw_efuse.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/osdep_service.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/osdep_service.c:24:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/osdep_service.c:24:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/os_intfs.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/os_intfs.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/os_intfs.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/usb_intf.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/usb_intf.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/usb_intf.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/usb_ops_linux.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/usb_ops_linux.c:21:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/usb_ops_linux.c:21:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_linux.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_linux.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_linux.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/xmit_linux.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/xmit_linux.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/xmit_linux.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/mlme_linux.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/mlme_linux.c:24:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/mlme_linux.c:24:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/recv_linux.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/recv_linux.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/recv_linux.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
  CC [M]  /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.o
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:35,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c:22:
/var/lib/dkms/rtl8192eu/1.0/build/include/wifi.h:1019: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service_linux.h:84,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/osdep_service.h:45,
                 from /var/lib/dkms/rtl8192eu/1.0/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
/var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c: In function &#8216;rtw_spt_band_free&#8217;:
/var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c:288:20: warning: comparison between &#8216;enum nl80211_band&#8217; and &#8216;enum ieee80211_band&#8217; [-Wenum-compare]
  if(spt_band->band == IEEE80211_BAND_2GHZ)
                    ^~
/var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c:294:25: warning: comparison between &#8216;enum nl80211_band&#8217; and &#8216;enum ieee80211_band&#8217; [-Wenum-compare]
  else if(spt_band->band == IEEE80211_BAND_5GHZ)
                         ^~
/var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c: In function &#8216;rtw_get_systime_us&#8217;:
/var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.c:362:2: error: implicit declaration of function &#8216;get_monotonic_boottime&#8217;; did you mean &#8216;getboottime&#8217;? [-Werror=implicit-function-declaration]
  get_monotonic_boottime(&ts);
  ^~~~~~~~~~~~~~~~~~~~~~
  getboottime
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:286: /var/lib/dkms/rtl8192eu/1.0/build/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [Makefile:1584: _module_/var/lib/dkms/rtl8192eu/1.0/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.0.0-15-generic'
make: *** [Makefile:1700: modules] Error 2
```
Any help would be appreciated.
Edit:
Wireless Info:[http://paste.ubuntu.com/p/PXQzB2Bg9z/](http://paste.ubuntu.com/p/PXQzB2Bg9z/)

---

### Post by slickymaster on 2019-05-27
[I]Thread moved to **Networking & Wireless**.

[/I]Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

---

### Post by razorrzr0 on 2019-05-27
> **slickymaster said:**
> [I]Thread moved to **Networking & Wireless**.

[/I]Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

here's the info you asked for:- [http://paste.ubuntu.com/p/PXQzB2Bg9z/](http://paste.ubuntu.com/p/PXQzB2Bg9z/)

---

### Post by chili555 on 2019-05-27
You have an internal wireless device which is driven by the normally reliable driver iwlwifi. I suspect that it drops and reconnects as it is constantly looking for a better connection; much like my ex-girlfriend.

It does so, I am quite confident, because the are two access points with the same name:

```
SSID  BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
FH2   <MAC 'FH2' [AC1]>  Infra  6     2437 MHz  130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2      yes     *      
FH2   <MAC 'FH2' [AC2]>  Infra  149   5745 MHz  270 Mbit/s  44      &#9602;&#9604;__  WPA2      no             

```
I believe that these are the 2.4 gHz and 5 gHz segments of your router. Please note that a signal strength of 60/100 is not excessively low.

I suspect that, in order to counter the drops, you purchased the USB wireless and you are now shocked to see that it has even *lower* signal strength. Frankly, this is to be expected, as the antenna on the USB is far, far smaller than the antenna for your internal device. Usually, the antenna for an internal wireless device wraps around the entire screen.

I think you can alleviate the dropping by renaming the two segments in your router, something like FH2.4 and FH5. Reboot the router, connect the wireless to FH2.4 and please report back.

---

### Post by razorrzr0 on 2019-05-27
> **chili555 said:**
> You have an internal wireless device which is driven by the normally reliable driver iwlwifi. I suspect that it drops and reconnects as it is constantly looking for a better connection; much like my ex-girlfriend.

It does so, I am quite confident, because the are two access points with the same name:

```
SSID  BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
FH2   <MAC 'FH2' [AC1]>  Infra  6     2437 MHz  130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2      yes     *      
FH2   <MAC 'FH2' [AC2]>  Infra  149   5745 MHz  270 Mbit/s  44      &#9602;&#9604;__  WPA2      no             

```
I believe that these are the 2.4 gHz and 5 gHz segments of your router. Please note that a signal strength of 60/100 is not excessively low.

I suspect that, in order to counter the drops, you purchased the USB wireless and you are now shocked to see that it has even *lower* signal strength. Frankly, this is to be expected, as the antenna on the USB is far, far smaller than the antenna for your internal device. Usually, the antenna for an internal wireless device wraps around the entire screen.

I think you can alleviate the dropping by renaming the two segments in your router, something like FH2.4 and FH5. Reboot the router, connect the wireless to FH2.4 and please report back.
Nah, it gives me nearly(most of the time) full signals on Windows but on Linux it shows one bar for every connections.
(unrelated stuff below)
I managed to fixed it previously on 18.04, but that was on a different system and i can't find the forum i found the solution from.
and where i am from there's no 5ghz wifi atm lol.

---

### Post by chili555 on 2019-05-27
> where i am from there's no 5ghz wifi atm lol.I believe there is no 5G cellular, but 5 gHz wifi is another thing entirely. There it is!> FH2   <MAC 'FH2' [AC2]>  Infra  149   [COLOR="#FF0000"]5745 MHz[/COLOR]  270 Mbit/s  44      &#9602;&#9604;__  WPA2      noYour wireless_info clearly shows that your internal Intel scans and sees it.

---

### Post by razorrzr0 on 2019-05-27
> **chili555 said:**
> I believe there is no 5G cellular, but 5 gHz wifi is another thing entirely. There it is!Your wireless_info clearly shows that your internal Intel scans and sees it.

From what I have seen, it's a driver problem cuz last time I installed a driver or a driver fix and did some modprobe command and it was fixed.
I can't find driver now, every driver I try to use gives that error (I have tried offical/ two alternatives).

---

### Post by razorrzr0 on 2019-05-28
Aight, Apparently the driver i tried to used doesn't works with DKMS. So the issue is fixed now, thanks for helping me.
(unrelated stuff below)
So the Fix was use make install instead of DKMS
```

[COLOR=#E8E6E3][FONT=&amp]sudo apt install git
git clone https://github.com/Mange/rtl8192eu-linux-driver.gitcd rtl8192eu-linux-driver
make
sudo make install
 sudo modprope -rv rtl8xxxu
sudo modprobe 8192eu
[/FONT][/COLOR]
```

---

