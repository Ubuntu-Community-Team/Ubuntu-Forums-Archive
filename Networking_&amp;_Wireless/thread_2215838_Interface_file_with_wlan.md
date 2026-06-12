---
title: "Interface file with wlan"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by hojkoff on 2014-04-08
I'm trying to get wlan working by editing the interface file. 

I've added the following

```
auto wlan0
iface wlan0 inet dhcp
wpa-ssid "SSID NAME IN HERE"
wpa-pask *XXXXXXXX*
```

But I can't get it to connect. Any ideas what I'm doing wrong?

Can anyone point to a manual for this? I can't find a definitive list of what is acceptable anywhere.

---

### Post by chili555 on 2014-04-08
> auto wlan0
iface wlan0 inet dhcp
wpa-ssid "SSID NAME IN HERE"
wpa-[COLOR="#FF0000"]pask[/COLOR] XXXXXXXXI think you mean wpa-psk. After you make that correction, then:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The -v for verbose may allow you to see some clue as to what's going wrong.

I also assume Network Manager is not running or is removed.

---

