---
title: "hostapd doesn't recognize ieee80211ac and ACS"
date: 2015-03-22
forum: Networking &amp; Wireless
---

### Post by bartgrefte on 2015-03-22
Just now I tried setting up an access point on the 5GHz band and it failed with this
```
Line 7: unknown configuration item 'ieee80211ac'
```
and this
```
ACS was disabled on your build, rebuild hostapd with CONFIG_ACS=y or set channel
```
Both are features that I would've expected to be available (out of the box I mean), but apparently they are not.
Is there a reason for that?

In addition to the above, for some reason the bandwidth isn't too high. Windows says 144.4Mbps at the statuswindow of the wireless connection (AR9380), however iperf says 47.9Mbps. Already disabled powersave, that wasn't it and it can't be nearby networks since there's only 1 (barely registering) on the 5GHz band while there are over 200 more on the 2.4GHz band...
Did I mis anything in the hostapd.conf?```
interface=wlan1
driver=nl80211
ssid=test5g
channel=36
hw_mode=a
ieee80211n=1
#ieee80211ac=1
ieee80211d=1
ieee80211h=1
wmm_enabled=1
auth_algs=1
wpa=2
wpa_passphrase=******
wpa_pairwise=CCMP
rsn_pairwise=CCMP
country_code=NL
ieee80211d=1
ht_capab=[SHORT-GI-20][SHORT-GI-40][TX-STBC][RX-STBC1][DSSS_CCK-40]
```The wifi card set up as access point is a [R11e-5HacD (QCA9882)](http://routerboard.com/R11e-5HacD) build into a computer running Ubuntu Server 14.10.

---

