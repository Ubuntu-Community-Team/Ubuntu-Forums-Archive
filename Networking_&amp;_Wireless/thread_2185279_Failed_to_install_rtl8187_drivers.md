---
title: "Failed to install rtl8187 drivers"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by bradleybaldwin on 2013-11-01
Hello,
I am trying to install the rtl8187 driver for my AWUS036H card by following this tutorial [http://www.aircrack-ng.org/doku.php?id=r8187#general](http://www.aircrack-ng.org/doku.php?id=r8187#general), but when I run make I get this error:

rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/3.11.0-12-generic/build M=/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
In file included from /home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:17:0:
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:986:24: error: field ‘ps_task’ has incomplete type
  struct tasklet_struct ps_task;
                        ^
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac_rtl7’:
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1512:3: error: implicit declaration of function ‘tasklet_schedule’ [-Werror=implicit-function-declaration]
   tasklet_schedule(&ieee->ps_task);
   ^
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init_rtl7’:
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2229:2: error: implicit declaration of function ‘tasklet_init’ [-Werror=implicit-function-declaration]
  tasklet_init(&ieee->ps_task,
  ^
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_wpa_set_encryption_rtl7’:
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2474:3: error: implicit declaration of function ‘request_module’ [-Werror=implicit-function-declaration]
   request_module("ieee80211_crypt_wep_rtl");
   ^
/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2503:3: error: implicit declaration of function ‘try_module_get’ [-Werror=implicit-function-declaration]
   if (new_crypt->ops && try_module_get(new_crypt->ops->owner))
   ^
cc1: some warnings being treated as errors
make[3]: *** [/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Error 1
make[2]: *** [_module_/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bradley/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2


Any help would be appreciated.

I am running Ubuntu 13.04 with the latest updates.

Thanks,
Bradley

---

### Post by chili555 on 2013-11-01
> rtl8187_linux_26.1010.0622.[COLOR="#FF0000"]2006[/COLOR]That file is old, old, old and will never, ever work in 13.10, which you have and not 13.04. rtl8187 is built in:> chili@Think410:~$ modinfo [COLOR="#FF0000"]rtl8187[/COLOR]
filename:       /lib/modules/[COLOR="#FF0000"]3.11.0-12-generic[/COLOR]/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     AF412C44DACDC2D28C5DF42
<snip>
We know nothing about aircrack and don't want to know and so we are unable to answer as to how to patch rtl8187 for packet corruption or whatever.

---

