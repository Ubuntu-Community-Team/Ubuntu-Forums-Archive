---
title: "Connecting to the internet - help please /interfaces configuration"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by gazz1982 on 2008-05-31
I have installed the drivers I need but I cant configure the /interfaces file correctly I have this code:

auto lo
iface lo inet loopback
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid *ssidname*
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=********
pre-up iwpriv wlan0 set EncrpType=TKIP
auto wlan0

however I am using WEP with a dynamic ip address, how do I ammend this to make it work?

Thank you

Gary

---

### Post by chili555 on 2008-05-31
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid urlilrouter
wireless-key urWEPkey
```Post back if you get stuck.

---

### Post by gazz1982 on 2008-05-31
nearly worked - it said:

No DHCPOFFERS recieved.
No working lenses in persistant database - sleeping
grep: /etc/resolv.conf: no such file or directory
any ideas?

---

### Post by gazz1982 on 2008-05-31
ah do I need ndiswrapper?

I'm using a belkin usb stick to connect to my wireless router

---

### Post by gazz1982 on 2008-05-31
dont worry it works needed rebooting!

---

