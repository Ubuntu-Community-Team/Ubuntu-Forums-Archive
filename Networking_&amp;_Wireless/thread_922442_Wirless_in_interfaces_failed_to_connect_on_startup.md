---
title: "Wirless in interfaces failed to connect on startup."
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by OnlyWhisky on 2008-09-17
Hello, in my /etc/network/interfaces I have:
> auto lo ath0

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid home_net
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk keygoes here

ath0 doens't connect to home_net on startup, but if I type:
> sudo /etc/init.d/networking restart
then it connect.

Why could that be?

---

### Post by OnlyWhisky on 2008-09-17
Sorry, I found the answer, it is ubuntu bug.

---

