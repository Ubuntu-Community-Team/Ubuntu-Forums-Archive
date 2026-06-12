---
title: "Ubuntu 14.04 beta Lenovo G505 wireless problem after resume"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by marian-hromiak on 2014-04-17
I had a problem after awake from suspend with ath9k, wpa_supplicant and NetworkManager. After resume NetworkManager tried to connect to wifi, disconnect and again. I found this post in syslog:
wpa_supplicant[1944]: wlan0: Reject scan trigger since one is already pending
wpa_supplicant[1944]: wlan0: Failed to initiate AP scan
wpa_supplicant[1944]: wlan0: Reject scan trigger since one is already pending
wpa_supplicant[1944]: wlan0: Failed to initiate AP scan
wpa_supplicant[1944]: wlan0: Reject scan trigger since one is already pending
wpa_supplicant[1944]: wlan0: Failed to initiate AP scan
wpa_supplicant[1944]: wlan0: Reject scan trigger since one is already pending
wpa_supplicant[1944]: wlan0: Failed to initiate AP scan
wpa_supplicant[1944]: wlan0: Reject scan trigger since one is already pending
wpa_supplicant[1944]: wlan0: Failed to initiate AP scan.

I tried unload module, restart NetworkManager service, etc, but nothing of this help, except kill wpa_supplicant. I hope, this post help somebody else.

---

