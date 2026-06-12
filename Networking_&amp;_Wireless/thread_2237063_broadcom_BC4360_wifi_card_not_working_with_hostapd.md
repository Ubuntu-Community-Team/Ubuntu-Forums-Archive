---
title: "broadcom BC4360 wifi card not working with hostapd"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by swchoi-choi on 2014-07-30
```

router@router:~/wifi$ sudo hostapd -B /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
nl80211: Could not configure driver mode
nl80211 driver initialization failed.
hostapd_free_hapd_data: Interface eth1 wasn't started

```
```

interface=eth1
driver=nl80211
ssid=dontMessWithVincentValentine
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=KeePGuessinG
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```

I'm using the new Asus PCE-AC68 and am told it's uses the BCM4360 chipset. I do have it functioning as a wifi card but not as a wireless ap.
I compiled the driver using the lastest source code I obtained from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).
This is on ubuntu 14.04 and is using the CFG80211 API. I can't use adhoc wireless because android doesn't support even though it's based on linux.

---

