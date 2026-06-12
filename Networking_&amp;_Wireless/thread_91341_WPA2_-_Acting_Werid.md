---
title: "WPA2 - Acting Werid"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by firestrife2382 on 2005-11-17
I've manage to set up WPA2 and get it working but for some werid reason: on the top taskbar indicated that the wireless connection signal strength is at full then disconnect back n forth every 1 mins or so. However, i'm able to browser the web just fine without interuption. 

Here's my wpa_supplicant.conf

```
network={
       ssid="transporter2382"
       scan_ssid=1
       proto=RSN
       pairwise=TKIP
       group=TKIP
       key_mgmt=WPA-PSK
       psk="XXXXXXXXXXX"
}
```

---

### Post by firestrife2382 on 2005-11-19
Never mind, I solved it by updating my ieee80211 to version 1.1.6, ipw2200 firmware to 2.4 and ipw2200 driver to 1.0.8 :p

---

