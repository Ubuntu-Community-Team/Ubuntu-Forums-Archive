---
title: "Wifi Connection Drop Solution (WPA Group Rekeying)"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by szm428 on 2015-01-17
I constantly get the following messages from syslog.

```
Jan 17 09:36:19 wpa_supplicant[1168]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 17 09:36:20 wpa_supplicant[1168]: wlan0: WPA: Group rekeying completed with 10:fe:ed:79:85:56 [GTK=CCMP]
Jan 17 09:38:19 wpa_supplicant[1168]: message repeated 119 times: [ wlan0: WPA: Group rekeying completed with xx:xx... [GTK=CCMP]]
Jan 17 09:38:19 wpa_supplicant[1168]: wlan0: CTRL-EVENT-SCAN-STARTED 

```

If you receive similar messages and your wireless connection  continuous breaks , do the following:

Go to your modem wifi security settings

if [COLOR=#000080]WPA/WPA2 Group Key Update Period[/COLOR] zero or disabled, you must change it.

Set WPA/WPA2 Group Key Update Period to 86400

Save your settings and reboot your modem/router.

Now your problem is solved.

[IMG]http://i.hizliresim.com/LYlqGG.png[/IMG]

---

