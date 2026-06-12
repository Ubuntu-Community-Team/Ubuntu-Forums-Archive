---
title: "Advantages over wpa-supplicant?"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-08-18
Good day! I've configured my wireless hotspot and got the following question, the WLAN section in my /etc/network/interfaces looks like that:```
#Wireless Setup
auto ath0
iface ath0 inet manual
wireless-mode master
wireless-essid Home
wireless-key <my 128 bit HEX key>
wireless-keymode restricted

```Everything works cool, but I've read on the forum that people generally use wpa-supplicant and syntax like:```
#wpa-driver wext
#wpa-ssid home
#wpa-ap-scan 2
#wpa-proto RSN
#wpa-pairwise CCMP
#wpa-group CCMP
#wpa-key-mgmt WPA-PSK
#wpa-psk <password>

```Why is that? What are the general advantages of wpa-supplicant? Is it better? How about security?

Thank you!

---

