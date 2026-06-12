---
title: "Wifi authentication failure (code 37, &quot;does not want to use the mechanism&quot;)"
date: 2020-07-27
forum: Networking &amp; Wireless
---

### Post by aurimas-racas on 2020-07-27
Hi there! I am looking for help with Wifi issues.

I am staying at a temporary apartment (so I do not have access to the router to tweak its settings), and I cannot get my laptop to connect to the WiFi. My Android phone and another laptop (Mac) connect without any issues.

Looking at /var/log/syslog, it seems that the AP is rejecting the connection with a status code 37
```
Jul 27 10:24:54 m2r2 NetworkManager[1005]: <info>  [1595838294.3991] device (wlp8s0): supplicant interface state: disconnected -> scanning
Jul 27 10:24:54 m2r2 wpa_supplicant[1053]: wlp8s0: CTRL-EVENT-SSID-REENABLED id=0 ssid="ZH82"
Jul 27 10:24:54 m2r2 wpa_supplicant[1053]: wlp8s0: SME: Trying to authenticate with 18:e8:29:6d:83:41 (SSID='ZH82' freq=2462 MHz)
Jul 27 10:24:54 m2r2 kernel: [  123.936605] wlp8s0: authenticate with 18:e8:29:6d:83:41
Jul 27 10:24:54 m2r2 kernel: [  123.940669] wlp8s0: send auth to 18:e8:29:6d:83:41 (try 1/3)
Jul 27 10:24:54 m2r2 kernel: [  123.944809] wlp8s0: 18:e8:29:6d:83:41 denied authentication (status 37)
Jul 27 10:24:54 m2r2 NetworkManager[1005]: <info>  [1595838294.4359] device (wlp8s0): supplicant interface state: scanning -> authenticating
Jul 27 10:24:54 m2r2 wpa_supplicant[1053]: wlp8s0: CTRL-EVENT-AUTH-REJECT 18:e8:29:6d:83:41 auth_type=0 auth_transaction=2 status_code=37
Jul 27 10:24:54 m2r2 wpa_supplicant[1053]: wlp8s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="ZH82" auth_failures=2 duration=20 reason=CONN_FAILED
Jul 27 10:24:54 m2r2 NetworkManager[1005]: <info>  [1595838294.4689] device (wlp8s0): supplicant interface state: authenticating -> disconnected
```

Internet tells me that this status code stands for "Requested from peer STA as it does not want to use the mechanism", but I do not really know what that means and how to go about fixing it.

I attach my wireless info script outputs, thanks for any hints and suggestions in advance!
[ATTACH]286558[/ATTACH]

---

