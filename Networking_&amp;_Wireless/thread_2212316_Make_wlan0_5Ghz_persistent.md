---
title: "Make wlan0 5Ghz persistent"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by bianchirick on 2014-03-20
I have set my wlan0 to 5Ghz range with "iwconfig wlan0 freq 5G", I am using it as an access point, but the setting does not appear to be persistent. After a reboot it comes back up in 2.4Ghz mode. Is there a commend in /etc/network/interfaces I can set to make it persistent?

Current Config:
auto wlan0
iface wlan0 inet static
address 10.0.0.1
netmask 255.255.255.0

Thanks in Advance ,
Rick

Edit: I found the solution, I added "wireless-channel 149" to /etc/network/interfaces:

New Config:
auto wlan0
iface wlan0 inet static
address 10.0.0.1
netmask 255.255.255.0
wireless-channel 149[COLOR=black]
[/COLOR]

---

