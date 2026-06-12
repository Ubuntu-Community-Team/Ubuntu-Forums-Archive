---
title: "D-Link DWL G520M Help"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by ArritUK on 2008-11-08
Hi

I'm trying to get my wireless card working but I'm having  a few problems.

I know that the card is using the Atheros AR5513 chip and I've aquired the madwifi drivers.

However when I use the make command I get some errors appering

Checking requirements... ok. 
Checking kernel configuration... ok. 
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/david/Desktop/madwifi-0.9.4 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic' 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath/if_ath.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath/if_ath_pci.o 
  LD [M]  /home/david/Desktop/madwifi-0.9.4/ath/ath_pci.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath_hal/ah_os.o 
  HOSTCC  /home/david/Desktop/madwifi-0.9.4/ath_hal/uudecode 
  UUDECODE /home/david/Desktop/madwifi-0.9.4/ath_hal/i386-elf.hal.o 
  LD [M]  /home/david/Desktop/madwifi-0.9.4/ath_hal/ath_hal.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/amrr/amrr.o 
  LD [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/minstrel/minstrel.o 
  LD [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/onoe/onoe.o 
  LD [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/sample/sample.o 
  LD [M]  /home/david/Desktop/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/if_media.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_beacon.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_none.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_input.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_node.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_output.o 
  CC [M]  /home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o 
/home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave': 
/home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append' 
make[3]: *** [/home/david/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1 
make[2]: *** [/home/david/Desktop/madwifi-0.9.4/net80211] Error 2 
make[1]: *** [_module_/home/david/Desktop/madwifi-0.9.4] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' 
make: *** [modules] Error 2 

Any help will be very welcome

Thanks

---

