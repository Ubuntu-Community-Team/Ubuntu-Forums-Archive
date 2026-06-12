---
title: "[SOLVED] Help needed to change /network/interfaces"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Frenske on 2008-09-13
I need to change the interfaces file for network because we have a new internet provider and new passwords. I have uninstalled the network manager because of problems with the drivers for Belkin (long story).

The previous internet connection required a WPA key and the new one a WEP. How do I change the old interfaces file to make it suitable for the new WEP one? I have tried to change various things but nothing works (being a noob), but using iwlist wlan0 scan I can see the network I want to log on:

The old code:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
  pre-up ifconfig wlan0 up
  pre-up iwconfig wlan0 mode managed
  pre-up iwpriv wlan0 set EncrypType=TKIP
  pre-up iwpriv wlan0 set AuthMode=WPAPSK
  pre-up iwconfig wlan0 essid 2WIRE078
  pre-up iwpriv wlan0 set WPAPSK="139484839"
  pre-up iwconfig wlan0 essid 2WIRE078
```

---

