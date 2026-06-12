---
title: "Connected to wifi but not showing any wifi network"
date: 2017-01-15
forum: Networking &amp; Wireless
---

### Post by sacherus on 2017-01-15
I'm connected to wifi but I don't see any wifi network: see the picture. Any clues? I will post any logs etc. what you need. It happens randomly.

[https://s23.postimg.org/3pxsbrfej/Screenshot_from_2017_01_15_23_52_49.png](https://s23.postimg.org/3pxsbrfej/Screenshot_from_2017_01_15_23_52_49.png)

---

### Post by wildmanne39 on 2017-01-15
Please use thumbnails or url's when posting images because many people have slow or limited connections

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by sacherus on 2017-01-15
I will remember about images.

Output from scripts:
[http://paste.ubuntu.com/23807679/](http://paste.ubuntu.com/23807679/)

---

### Post by wildmanne39 on 2017-01-15
I see a lot of things that may be causing issues, did your wifi ever have internet with ubuntu?

What are all these connections? do you need them?
```
ham0      no wireless extensions.

br-2fdef8ddea62  no wireless extensions.

veth88a3ad0  no wireless extensions.

br-60ea7de75b92  no wireless extensions.

docker0   no wireless extensions.

```
and these:
```
[[/etc/NetworkManager/system-connections/Wireless-N_00e0203f960e]] (600 root)
[connection] id=Wireless-N_00e0203f960e | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=Wireless-N_00e0203f960e
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Chomiczowka Pierwsza Milosc]] (600 root)
[connection] id=Chomiczowka Pierwsza Milosc | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=Chomiczowka Pierwsza Milosc
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link Dir635 1]] (600 root)
[connection] id=D-Link Dir635 1 | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=D-Link Dir635
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link Dir635]] (600 root)
[connection] id=D-Link Dir635 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=D-Link Dir635
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lipinskiego28]] (600 root)
[connection] id=lipinskiego28 | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=lipinskiego28
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AJakiJestTwojCelWZyciu?]] (600 root)
[connection] id=AJakiJestTwojCelWZyciu? | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=AJakiJestTwojCelWZyciu?
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/starcraft]] (600 root)
[connection] id=starcraft | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=starcraft
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP 1]] (600 root)
[connection] id=AndroidAP 1 | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NEXT42]] (600 root)
[connection] id=NEXT42 | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=NEXT42
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=dlink
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ SOHO INTERNET]] (600 root)
[connection] id=\sSOHO INTERNET | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=\sSOHO INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETIASPOT-A0E3B0]] (600 root)
[connection] id=NETIASPOT-A0E3B0 | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=NETIASPOT-A0E3B0
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_A44484]] (600 root)
[connection] id=TP-LINK_A44484 | type=wifi | autoconnect=false | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=TP-LINK_A44484
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Lajkonik]] (600 root)
[connection] id=Lajkonik | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=Lajkonik
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_53B54F]] (600 root)
[connection] id=TP-LINK_53B54F | type=wifi | permissions=user:sacherus:;
[wifi] mac-address=<MAC 'wlp2s0' [IF7]> | mac-address-blacklist= | ssid=TP-LINK_53B54F
[ipv4] method=auto
[ipv6] method=auto
```
it could not hurt if we can clean those up.

Please run:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot
Thanks

---

### Post by sacherus on 2017-01-16
- I always have connection to the Internet - as you can see it's GUI bug
- Bridges docker/docker-compose and tunnel to the hamachi 
- Why should I have change powersaving settings?

---

### Post by wildmanne39 on 2017-01-17
Let's do:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Reboot if asked, does that help? if not do:
```
sudo apt-get install --reinstall network-manager-gnome
```
and you can try:
```
sudo systemctl restart NetworkManager.service
```
If that does not help then I am out of ideas because as long as you can connect to the internet it really is not a wireless issue.

---

### Post by sacherus on 2017-01-21
It doesn't help at all :(. I think it's more indicator/GUI issue than wifi.

---

