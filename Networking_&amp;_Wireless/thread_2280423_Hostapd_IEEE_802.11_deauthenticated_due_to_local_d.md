---
title: "Hostapd: IEEE 802.11: deauthenticated due to local deauth request"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by Amit_Thakur on 2015-05-30
Hi,

I want to create Hotspot using WiFi USB adapter. I have a wired LAN (eth0) and want to share it using hotspot.

I built hostapd from the source and followed the steps: [https://wireless.wiki.kernel.org/en/users/documentation/hostapd](https://wireless.wiki.kernel.org/en/users/documentation/hostapd)

When I run the hostapd, my android device is able to detect the wifi signal but cannot authorize for long. I get following message on the PC console:



> sudo ./hostapd /etc/hostapd/hostapd.conf 
Configuration file: /etc/hostapd/hostapd.conf
nl80211: Could not re-add multicast membership for vendor events: -2 (No such file or directory)
wlan1: interface state UNINITIALIZED->COUNTRY_UPDATE
Using interface wlan1 with hwaddr c4:e9:84:07:87:95 and ssid "DellWiFi"
wlan1: interface state COUNTRY_UPDATE->ENABLED
wlan1: AP-ENABLED 
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: authenticated
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: associated (aid 1)
WPA: wpa_sm_step() called recursively
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: deauthenticated due to local deauth request
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: authenticated
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: associated (aid 1)
WPA: wpa_sm_step() called recursively
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: deauthenticated due to local deauth request
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: authenticated
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: associated (aid 1)
WPA: wpa_sm_step() called recursively
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: deauthenticated due to local deauth request
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: authenticated
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: associated (aid 1)
WPA: wpa_sm_step() called recursively
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: deauthenticated due to local deauth request
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: authenticated
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: associated (aid 1)
WPA: wpa_sm_step() called recursively
wlan1: STA a0:86:c6:4d:9f:f6 IEEE 802.11: deauthenticated due to local deauth request
^Cwlan1: interface state ENABLED->DISABLED
wlan1: AP-DISABLED 
nl80211: deinit ifname=wlan1 disabled_11b_rates=0

**UPDATE: This script works perfectly :-) : [https://github.com/oblique/create_ap](https://github.com/oblique/create_ap)**

---

