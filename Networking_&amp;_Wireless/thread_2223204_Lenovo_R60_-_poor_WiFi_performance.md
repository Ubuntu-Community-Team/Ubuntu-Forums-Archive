---
title: "Lenovo R60 - poor WiFi performance"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by drechsel on 2014-05-09
Hi everybody,

the WiFI-performance of the R60 laptop with atheros chipset is poor - meaning: Very close to the rooter it's ok, but only a few meters away it gets unuseably slow, allthough the signal strength indicator says we're having a good signal strength. In the same location WiFi works without any trouble under windows.

The atheros seems to register correctly:

[   13.648286] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.648421] ath5k 0000:03:00.0: registered as 'phy0'
[   14.239153] ath: EEPROM regdomain: 0x62
[   14.239158] ath: EEPROM indicates we should expect a direct regpair map
[   14.239162] ath: Country alpha2 being used: 00
[   14.239164] ath: Regpair used: 0x62
[   14.483763] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.484273] ath5k: phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)

Frequently this message occurs:

[ 1409.104312] cfg80211: Calling CRDA to update world regulatory domain
[ 1413.192749] wlan0: authenticate with 24:65:11:ba:51:a2
[ 1413.197856] wlan0: send auth to 24:65:11:ba:51:a2 (try 1/3)
[ 1413.245561] wlan0: authenticated
[ 1413.248093] wlan0: associate with 24:65:11:ba:51:a2 (try 1/3)
[ 1413.250860] wlan0: RX AssocResp from 24:65:11:ba:51:a2 (capab=0x431 status=0 aid=2)
[ 1413.251602] wlan0: associated

Any suggestions are very welcome.

Cheers,
Wolf

---

### Post by drechsel on 2014-05-09
Sorry - changed the WiFi channel, and things are fine now.

Cheers

---

