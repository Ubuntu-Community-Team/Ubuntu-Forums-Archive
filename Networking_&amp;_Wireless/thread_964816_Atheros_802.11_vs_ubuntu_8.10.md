---
title: "Atheros 802.11 vs ubuntu 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by dudan on 2008-10-31
Hi, I have a problem with my wifi. I have Atheros 802.11 and it doesn`t work with Ubuntu 8.10. In system>administration>hardware drivers (it is maybe little bit another, I have Slovak version), I found note, that "driver is active, but currently not used". 
How can I use this driver? Or I must do something else? I tried madwifi, but when I had maked it, it wrote:
/home/michal/madwifi/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/michal/madwifi/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/michal/madwifi/net80211] Error 2
make[1]: *** [_module_/home/michal/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Chyba 2

then I found the patch on it, but it was able to patch only 1 thing out of 3. Even though, I had tried make it again, but it wrote

/home/michal/madwifi/net80211/ieee80211_input.c:3709: error: implicit declaration of function 'M_PWR_SAV_SET'
make[3]: *** [/home/michal/madwifi/net80211/ieee80211_input.o] Error 1
make[2]: *** [/home/michal/madwifi/net80211] Error 2
make[1]: *** [_module_/home/michal/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Chyba 2

Please help me, Notebook without wifi is ****:)

---

### Post by kgish on 2008-10-31
I just upgraded from 8.10 beta to 8.10 and had the very same problem. For 8.10 beta the madwifi stuff installed and ran without a hitch, however now when I run make I get the same error message as above. Help!

---

### Post by daffyduc on 2008-10-31
also in the same boat. 

mine says driver activated and IN USE but I cannot connect or get anything on the wireless card.

---

### Post by daffyduc on 2008-10-31
[http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros](http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros)

^ worked for me

---

