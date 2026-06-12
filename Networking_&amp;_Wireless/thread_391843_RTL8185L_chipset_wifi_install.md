---
title: "RTL8185L chipset wifi install"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by tbuss on 2007-03-23
I have a belkin wifi card with a rtl8185 chipset. I have tried to use ndiswrapper with BCM drivers and windoze native drivers....no luck. I have linux-restricted-modules installed but still no wifi. I have succesfully installed other wifi cards (d-link atheros and belkin with broadcom chipset) using linux-restricted-modules and ndiswrapper respectively.

lspci gives me this:
```
01:08.0 Ethernet controller: Belkin Unknown device 700f (rev 20
```) 

I did search and found the driver for this card on sourceforge (rtl818x-1.0.1-b.tar.gz)  After extracting the contents and running make, I get the following:

```
bea@ubuntuBea:~/rtl818x-1.0.1-b$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd`/net/ieee80211 CONFIG_IEEE80211=m CONFIG_IEEE80211_CRYPT=m CONFIG_IEEE80211_CRYPT_WEP=m CONFIG_IEEE80211_CRYPT_CCMP=m CONFIG_IEEE80211_CRYPT_TKIP=m CC="gcc -I`pwd`/include" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd`/drivers/net/wireless/rtl818x CONFIG_RTL818X=m CC="gcc -I`pwd`/include" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
WARNING: "ieee80211_wx_get_freq" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_ps_tx_ack" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_get_power" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_power" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
WARNING: "ieee80211_wx_get_name" [/home/bea/rtl818x-1.0.1-b/drivers/net/wireless/rtl818x/rtl818x.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
bea@ubuntuBea:~/rtl818x-1.0.1-b$ 
```

I'm not sure what all of this means, if anyone could point me in the right direction, I would greatly appreciate it.

---

### Post by tbuss on 2007-03-24
If anyone views this and you think you might have anything that will work, please post. I'm willing to try anything, if i have to re-install 50 times that's fine. I just need to find a way to get this to work. I have searched everywhere and I cannot find any useful info. Should I just forget about using the card and purchase one that is compatible with Linux? If you view this there is a chance that you are familair with the chipset or wifi configurations. If you have any suggestions please feel free to let me know. Thank You

---

### Post by bodhi.zazen on 2007-03-24
> **tbuss said:**
> If anyone views this and you think you might have anything that will work, please post. I'm willing to try anything, if i have to re-install 50 times that's fine. I just need to find a way to get this to work. I have searched everywhere and I cannot find any useful info. Should I just forget about using the card and purchase one that is compatible with Linux? If you view this there is a chance that you are familair with the chipset or wifi configurations. If you have any suggestions please feel free to let me know. Thank You

I'm not sure ~ I would keep going ~ 

Are you familiar with [checkinstall](https://help.ubuntu.com/community/CheckInstall) ?

perhaps give it a try ~ Install checkinstall (synaptic or what have you), then :

```
sudo checkinstall
```

---

