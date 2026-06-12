---
title: "compiling ieee80211"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by darkrider01 on 2006-10-13
Hi there

Does anyone know what maybe the issue here 

$ sudo make
Checking in /lib/modules/2.6.15-27-386/build/ for ieee80211 components...

CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT_WEP=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IEEE80211_SOFTMAC=m
CONFIG_IEEE80211_1_1_13=m
CONFIG_IEEE80211_1_1_13_CRYPT_WEP=m
CONFIG_IEEE80211_1_1_13_CRYPT_CCMP=m
CONFIG_IEEE80211_1_1_13_CRYPT_TKIP=m
Above definitions found.  Comment out? [y], n y
sed: can't read /lib/modules/2.6.15-27-386/build//build/.config: No such file or directory
make -C /lib/modules/2.6.15-27-386/build M=/home/pitt/Desktop/ieee80211-1.0.3 MODVERDIR=/home/pitt/Desktop/ieee80211-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/pitt/Desktop/ieee80211-1.0.3/ieee80211_module.o
/home/pitt/Desktop/ieee80211-1.0.3/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/pitt/Desktop/ieee80211-1.0.3/ieee80211_module.c:151: error: ‘struct ieee80211_device’ has no member named ‘tkip_countermeasures’
make[2]: *** [/home/pitt/Desktop/ieee80211-1.0.3/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/pitt/Desktop/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [modules] Error 2


I assume it's wrong path given here sed: can't read /lib/modules/2.6.15-27-386/build//build/.config: No such file or directory
That's true there is no such file or directory. This path should be /lib/modules/2.6.15-27-386/build/.config but how should i change it? Tried editing /usr/bin/make but... no success!

Thanks for any help.
Thks

---

