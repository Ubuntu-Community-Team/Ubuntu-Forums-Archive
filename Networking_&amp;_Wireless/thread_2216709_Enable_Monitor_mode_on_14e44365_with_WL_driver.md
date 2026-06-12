---
title: "Enable Monitor mode on 14e4:4365 with WL driver"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by The_Dinger on 2014-04-13
Hello,

My network card does not support the b43 driver and i would like to put it into monitor mode. I was wondering if this was somehow possible with the wl driver.

lspci -vnn | grep 14e4
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

airmon-ng start wlan0
```
Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
2524    NetworkManager
2632    wpa_supplicant
3348    dhclient
3708    dhclient
Process with PID 3708 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Broadcom    wl - [phy1]mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)


```

---

