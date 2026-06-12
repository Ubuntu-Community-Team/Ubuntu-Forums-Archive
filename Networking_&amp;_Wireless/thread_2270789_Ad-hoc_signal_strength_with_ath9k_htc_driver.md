---
title: "Ad-hoc signal strength with ath9k_htc driver"
date: 2015-03-25
forum: Networking &amp; Wireless
---

### Post by georgios2 on 2015-03-25
Hi, I need to get received signal strength in an ad-hoc network, but it seems that it doesn't work. 
**iwconfig** works perfectly giving all needed information when I am connected to a wifi router.

In case of ad-hoc I have tried to ping the laptop at which I want to get received signal strength to have some beacons.
Using aircrack it shows constantly signal strength -1 dbm even though it gets some beacons from ping.
It seems as if some modification on the driver is needed to make it possible.
I am using Ubuntu 14.04

Could someone please help?

---

### Post by aSmig on 2015-07-16
```
iw wlan0 station dump
```

Details here: [http://linuxwireless.org/en/users/Documentation/iw/__v69.html#line-129](http://linuxwireless.org/en/users/Documentation/iw/__v69.html#line-129)

You might also be able to use something similar to one of these depending on your kernel and driver:
```

cat /sys/kernel/debug/ieee80211/phy0/netdev:wlan0/stations/<peer-MAC>/last_signal
cat /sys/kernel/debug/ieee80211/phy0/stations/<peer-MAC>/rc_stats

```

[https://wireless.wiki.kernel.org/en/developers/documentation/mac80211/ratecontrol/minstrel](https://wireless.wiki.kernel.org/en/developers/documentation/mac80211/ratecontrol/minstrel) might also be interesting reading.

---

