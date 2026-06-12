---
title: "wpa_supplicant + ad-hoc + CCMP = dhcp problem"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by aditnsr on 2008-06-07
Hi,
im using wpa_supplicant to create ad-hoc network,
here is my wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant

ap_scan=2

network={
    ssid="homenetwork"
    mode=1
    proto=WPA
    key_mgmt=WPA-NONE
    pairwise=NONE
    group=TKIP
    psk="mysecretpassword"
}

using TKIP group cipher, evrything works fine, but if i use CCMP instead,
dhcp wont work. i must set IP manually..
anyone knows why?

---

### Post by aditnsr on 2008-06-10
can anybody help? ..

---

