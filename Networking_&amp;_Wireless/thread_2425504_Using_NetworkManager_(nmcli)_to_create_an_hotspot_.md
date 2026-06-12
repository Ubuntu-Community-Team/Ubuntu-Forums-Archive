---
title: "Using NetworkManager (nmcli) to create an hotspot broadcasting an hidden SSID"
date: 2019-08-26
forum: Networking &amp; Wireless
---

### Post by artynet on 2019-08-26
Hello folks,

as described in the subject I was wondering if I can hide the SSID of my freshly created hotspot by means of two simple **nmcli** commands :

```

nmcli device wifi hotspot ifname wlan0 con-name Hotspot ssid MySsid band bg channel 11 password 'mypassword'
nmcli con modify Hotspot ipv4.method shared ipv4.addresses 192.168.240.1/24
nmcli con up Hotspot

```

any pointers about that ? I still can't find the right option to add while creating the network...

              Kind Regards

---

