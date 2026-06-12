---
title: "no 5ghz AP mode on Intel wireless AC 7260"
date: 2018-12-22
forum: Networking &amp; Wireless
---

### Post by asaturn on 2018-12-22
I have an Ubuntu server running 14.04 on a "fitlet i" (AMD A4 Micro-6400T APU + AMD Radeon R3 Graphics @ 4x 1GHz) and I haven't upgraded the OS because the networking setup is flawless and I know newer Ubuntu changes the networking significantly.

The server uses the iwlwifi driver for the Intel chip, and running hostapd to deliver wireless in host/AP mode. This is my /etc/hostapd/hostapd.conf

```
auth_algs=1
beacon_int=50

#channel=36 #for N/5ghz
channel=11

#disassoc_low_ack=1
driver=nl80211

# Operation mode (a = IEEE 802.11a (5 GHz), b = IEEE 802.11b (2.4 GHz), G = G
# hw_mode=a
hw_mode=g

# wme_enabled=1

# wifi N
#ieee80211n=1

ht_capab=[HT40-][SHORT-GI-20][SHORT-GI-40][DSSS_CCK-40][DSSS_CCK-40][DSSS_CCK-40]

#ieee80211d=1   # allow country freq only
country_code=US # country code
#ieee80211ac=1  # 802.11ac support - this shows up as not an option?
#vht_oper_centr_freq_seg0_idx=42 - also not supported?

interface=wlan0
bridge=br0
require_ht=1

ssid=magi
wmm_enabled=1   # QoS support
wpa=2           # WPAv2 only
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
wpa_passphrase=passwordhere
```

Aside from writing my own driver, are there any ways to get 5ghz wireless out of this thing?

---

### Post by praseodym on 2018-12-23
Try a newer kernel with an updated driver and firmware

---

### Post by asaturn on 2018-12-23
Will the latest updates blow up my network config?

---

