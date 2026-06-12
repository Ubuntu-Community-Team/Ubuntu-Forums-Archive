---
title: "Trying to install wifi drivers.. Or maybe my issue is with OBS I don't know."
date: 2022-10-11
forum: Networking &amp; Wireless
---

### Post by peaceulautistic on 2022-10-11
Not having a great time with my [laptop]("https://support.hp.com/us-en/document/c06057260") (the link here is which laptop I have). I took it from windows to Ubuntu after my windows was acting slow and buggy even after 2 separate refresh to factory. I was having a great time with Ubuntu until I tried to do something to let me route audio from apps however I wanted to whatever audio device I wanted to unsuccessfully. I decided to reinstall Ubuntu. I had had my first install for a few months. It was going great with the reinstall. Until I tried to stream using OBS 28.0.3.

[This is my laptop's information just in case you need this for the troubleshooting (the summary, operating system and kernel modules as output by the app hardinfo)]("https://pastebin.com/0y33hwGz") I've done enough troubleshoot googling on things in my lifetime to know what sort of stuff may or may not be useful for you all.


I don't know if it's OBS 28.0.3 or if it's my WiFi driver not being installed but when I try to use OBS my WiFi connection will cut out with a question mark on the WiFi icon. Sometimes the WiFi will just get really really slow while being fast on my phone. I don't know what else to do.


The being said now, I don't remember which GIT I cloned but now, I have a git clone that is trapped. I've tried all the commands I've found online for cleaning it out but it won't go away. So I cannot clone any other GITs with the drivers listed. I'll show more about that near the end.


Here's a few photos to sort of show my issues here and what I'm actively trying to do. Before I start: I followed [this]("https://fostips.com/realtek-wifi-drivers-ubuntu-linux-mint/") to a T (using the synaptic package manager) with it working until I get to the reboot step which would make it so when I tried to connect to my WiFi it would be in a state of "connecting" until it would just give up. That's when I followed the uninstall and it reverted back to working unless I tried to stream. I asked on Reddit and someone said I should try [this]("https://github.com/smlinux/rtl8723de") so I did. The second thing I tried is what I am needing help with.


[IMG]https://preview.redd.it/8vp6vr8js9t91.png?width=786&format=png&auto=webp&983c03bb[/IMG]
[[img]https://i.postimg.cc/sgv6SzK9/Screenshot-from-2022-10-11-18-31-03.png[/img]](https://postimages.org/) What I tried and what I was told by my terminal.


This is what was in the file it asked me to look at for more information:
> DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 5.15.0-48-generic (x86_64)
Tue Oct 11 06:29:22 PM MDT 2022
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-48-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-48-generic'
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_security.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_security.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_security.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_debug.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_debug.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_debug.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_io.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_io.c:52:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_io.c:52:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_query.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_212 85.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_query.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_query.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_set.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_set.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_set.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ieee80211.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ieee80211.c:25:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ieee80211.c:25:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/../hal/phydm/phydm_types.h:177,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/../hal/phydm/phydm_precomp.h:24,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/hal_data.h:25,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/../hal/phydm/phydm_types.h:177,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/../hal/phydm/phydm_precomp.h:24,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/hal_data.h:25,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.c: In function ‘mgt_dispatcher’:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.c:1464:20: warning: this statement may fall through [-Wimplicit-fallthrough=]
1464 | if (check_fwstate(pmlmepriv, WIFI_AP_STATE) == _TRUE)
| ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.c:1469:9: note: here
1469 | case WIFI_ASSOCREQ:
| ^~~~
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mi.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mi.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mi.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_wlan_util.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_wlan_util.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_wlan_util.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_vht.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_vht.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_vht.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_pwrctrl.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_pwrctrl.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_pwrctrl.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_rf.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_rf.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_rf.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_recv.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_recv.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_recv.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sta_mgt.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sta_mgt.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sta_mgt.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ap.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ap.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ap.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_xmit.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_xmit.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_xmit.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_p2p.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_p2p.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_p2p.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_tdls.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:35,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_tdls.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/wifi.h:1006: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
1006 | #define IEEE80211_MAX_AMPDU_BUF 0x40
|
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:86,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_tdls.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
1703 | #define IEEE80211_MAX_AMPDU_BUF 0x100
|
CC [M] /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_br_ext.o
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_br_ext.c:25:18: fatal error: net/ipx.h: No such file or directory
25 | #include <net/ipx.h>
| ^~~~~~~~~~~
compilation terminated.
make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_br_ext.o] Error 1
make[1]: *** [Makefile:1884: /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-48-generic'
make: *** [Makefile:1884: modules] Error 2


So I'm not sure what happened with the whole thing as I don't understand any of this.
I thought maybe it was the files I was using? So I removed them and tried other GITs of the drivers with the same results... I don't know what I did wrong.
I tried to delete it the last time like I had been successful in doing until this happened:

[IMG]https://preview.redd.it/oya6yhjnw9t91.png?width=786&format=png&auto=webp&11830e31[/IMG]
[[img]https://i.postimg.cc/MGtnSk2N/Screenshot-from-2022-10-11-18-56-13.png[/img]](https://postimages.org/)I don't know where the folder goes when I run git clone so I don't know where to go to delete it. I used a different git to get another version of the file stuff that I was seeing when I searched the error in their issues section on the git.


This is very frustrating.
My level of knowledge BTW is follow what the person posts, pray to god it works and cry if it doesn't. I know I need sudo. I know how to use apt-get. That's about it so make it as easy to follow as possible thank you much! Right now I have nothing installed and the WiFi is working okay but as soon as I try to use OBS 28.0.3 the WiFi will die on me again with the question mark in the connection icon. I never tried using OBS on my laptop prior to 28 being launched. I was using my iMac that is only able to go to 10.13.6 and no further. I wanted to run OBS 28 which is incompatible with my iMac so I tried my laptop and now it's not working and I'm at the end of my rope.

---

### Post by chili555 on 2022-10-12
> when I try to use OBS my WiFi connection will cut out with a question mark on the WiFi icon.Then it is obvious that you have a driver for your device. Trying to install an older, moldy antique driver won't help. It is not yet clear that installing *any* substitute driver is helpful.

Let's remove the antique:

```
cd ~
sudo rm -r rtl8723de
```I suspect that your issue is with the settings on your wireless router. 

Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement? 

Here is a very good reference: [https://www.smallnetbuilder.com/wireless/wireless-features/33228-wi-fi-ping-spikes-causes-and-fixes](https://www.smallnetbuilder.com/wireless/wireless-features/33228-wi-fi-ping-spikes-causes-and-fixes)

---

