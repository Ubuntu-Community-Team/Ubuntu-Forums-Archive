---
title: "Roaming Problems on Broadcom BCM43228 [14e4:4359], Ubuntu 14.04"
date: 2015-08-27
forum: Networking &amp; Wireless
---

### Post by cifera on 2015-08-27
Hey,

I have problems with the roaming network at my uni ('eduroam'):

Often I can't connect at all after repeated failed connection attempts with password prompts every so often. 
Sometimes I get errors like:

```

[Don Aug 27 13:50:47 2015] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = [MAC1]   profile =[MAC2]
[Don Aug 27 13:50:47 2015] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = [MAC1]   profile =[MAC2]
[Don Aug 27 13:54:47 2015] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = [MAC2]   profile =[MAC1]
[Don Aug 27 13:54:47 2015] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = [MAC2]   profile =[MAC1]
[Don Aug 27 14:10:47 2015] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = [MAC1]   profile =[MAC2]
[Don Aug 27 14:10:47 2015] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = [MAC1]   profile =[MAC2]

```

and 
```

[Don Aug 27 14:14:13 2015] ERROR @wl_dev_intvar_get : error (-1)
[Don Aug 27 14:14:13 2015] ERROR @wl_cfg80211_get_tx_power : error (-1)

```
which I just had but I have a connection.
Sometimes I get
```
[Die Aug 25 16:50:58 2015] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)

```

```
ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
```
which may break the connection.

I have already tried some things and am not sure how to revert these (drivers, blacklist etc.) sorry!

Attached is the wireless-info.txt. 
Please help, thank you!

Edit: I should add that I don't have problems with other networks e.g. at home.

---

### Post by martine.ginette on 2015-11-09
Same problem here. Any solution?

---

### Post by George_Hardy on 2015-11-09
my problem with this adapter (hp 840), is that it wont wake up after i resume the laptop from a sleep.  i have to disable and then re-enable networking to get the wifi to come back up.

---

