---
title: "Script to add WiFi settings with VPN"
date: 2015-11-26
forum: Networking &amp; Wireless
---

### Post by danne33 on 2015-11-26
I am using Ubuntu 14.04.
I am trying to make a private script that add WiFi settings to the computer.

For instance, the following command connects to WiFi that the wlan can spot:
```
nmcli d wifi connect <WiFiSSID> password <WiFiPassword> iface wlan0
```

But how can I add WiFi settings that is outside wlans reach?
For example: wifi settings for workplace, girlfriends house, family members houses and so on.
It would be great if it was possible to assign each WiFi setting with an particular VPN server.

Example of final version could be:
```
nmcli d wifi add <WiFiSSID-Work> password <WiFiPassword> iface wlan0 vpn 4
nmcli d wifi add <WiFiSSID-brother> password <WiFiPassword> iface wlan0 vpn 1
nmcli d wifi add <WiFiSSID-sister> password <WiFiPassword> iface wlan0 vpn 1
nmcli d wifi add <WiFiSSID-Girlfriend> password <WiFiPassword> iface wlan0 vpn 4
```

---

### Post by michi1983 on 2015-11-26
Hi,

why would you want to do that if I may ask?
Whenever you enter a Wifi network your credentials get stored in the network manager
```
/etc/NetworkManager/system-connections
```
So why would you want to do that manually?

---

### Post by danne33 on 2015-11-26
> **michi1983 said:**
> Hi,

why would you want to do that if I may ask?
Whenever you enter a Wifi network your credentials get stored in the network manager
```
/etc/NetworkManager/system-connections
```
So why would you want to do that manually?

I travel a lot and have several computers.
Tend to sell old computers and buy new computers often. (Need to get the latest)
One of my computer have 20+ credentials. My wish is to avoid retyping them every time.
It doesn't work to copy paste "/etc/NetworkManager/system-connections".

---

### Post by michi1983 on 2015-11-27
Hm, it's from a time ago but maybe it still applies?
[http://ubuntuforums.org/showthread.php?t=1043039](http://ubuntuforums.org/showthread.php?t=1043039)

---

