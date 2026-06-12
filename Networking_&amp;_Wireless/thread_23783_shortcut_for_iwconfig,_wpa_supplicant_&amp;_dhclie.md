---
title: "shortcut for iwconfig, wpa_supplicant &amp; dhclient ?"
date: 2005-04-04
forum: Networking &amp; Wireless
---

### Post by kixvn on 2005-04-04
currently if I want to use the wireless connection, I must first change the essid and mode of the wireless interface

**iwconfig eth0 essid abc mode 0**

then activate wpa_supplicant

**wpa_supplicant -i eth0 -c /etc/wpa_supplicant.conf -Dipw2100**

and then run DHCP client

**dhclient**

can someone tell me some faster way to accomplish this ? I did a search and it seems I should edit /etc/network/interfaces or /etc/dhcp3/dhclient.conf . But I can't figure exactly what the changes must be

Thanks

---

### Post by prio on 2005-04-04
I have the following in my /etc/network/interfaces file

auto wlan0
iface wlan0 inet dhcp
wireless_mode infrastructure
wireless-essid myssid

Typing *ifup wlan0* then brings up my connection. If you are using the linux-wlan-ng drivers you then add wep information to the */etc/wlan/wlancfg-myssid* file. Copy the wlancfg-DEFAULT file and change it approriately. Not sure about other drivers. I think the Administration->networking application can deal with most other wireless cards. (Those not using the wlan-ng drivers)

---

