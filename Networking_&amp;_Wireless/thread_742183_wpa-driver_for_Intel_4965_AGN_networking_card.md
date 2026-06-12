---
title: "wpa-driver for Intel 4965 AGN networking card"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by kkjaergaard on 2008-04-01
I have an Intel 4965 AGN networking card and
```
wpa-driver **wext**
```
in /etc/network/interfaces. Should I use a different driver? (Intel writes about the iwlwifi driver on [their website]("http://intellinuxwireless.org/?p=iwlwifi"))

---

### Post by toff63 on 2008-04-03
Hi,

    Had you tried to do what is written here [http://ubuntuforums.org/archive/index.php/t-574958.html](http://ubuntuforums.org/archive/index.php/t-574958.html)
It worked for me.

I have just added this to the /etc/network/interfaces

auto wlan0
          iface wlan0 inet dhcp
          wpa-driver wext
          wpa-ssid your-network-ssid
          wpa-proto WPA
          wpa-key-mgmt WPA-PSK
          wpa-psk your-wpa-key-in-hexa

to have your your-wpa-key-in-hexa with
wpa_passphrase yourSSID youy-key

I hope it will work for you.

---

