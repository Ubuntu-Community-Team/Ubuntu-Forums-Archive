---
title: "wpa connaction"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by avior on 2015-03-18
hellow guys i want to connect to my wifi connaction with my ubuntu.
my wifi lock with WPA2 method


i tried same command like :


sudo wpa_passphrase avior_2.4 >>/etc/wpa_supplicant.conf


>/etc/wpa_supplicant.conf:


ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=netdev
update_confige=1
network={
               ssid="avior_2.4"
               scan_ssid=1
               pairwise=TKIP
               key_mgmt=WPA-PSK
               proto=WPA
psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
}


wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w
>>successfuly initialized wap_supplicant
>>ioctl[SIOCSIWENCODEEXT]: Invalid argument
>>ioctl[SIOCSIWENCODEEXT]: Invalid argument
>>ioctl[SIOCSIWSCAN]: Resource is temporarilt unavailable
>>ioctl[SIOCSIWSCAN]: Device or resource busy 


and it is not work

---

