---
title: "[WPA] /etc/network/interfaces does not work"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by sotanez on 2008-10-09
Hi.
I'm trying to configure the interfaces file to connect to a WPA-PSK encrypted wifi with my rt2500 (ra0 interface).

This is the interfaces file:

------------------------
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto ra0
iface ra0 inet dhcp
wireless-essid adh
wireless-mode managed
wireless-channel 5
pre-up ifconfig ra0 up
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid adh
pre-up iwpriv ra0 set WPAPSK=whatever
------------------------------------------

When I enter /etc/init.d/networking restart it does not work: dchp does not find any offers.
Then, if I enter the iwpriv commands by hand and after that I enter dhclient ra0 it DOES work.
I think there is something wrong with the interfaces file, but I cannot find the problem.
Any ideas?
Thank you and sorry for my English.

PD: I am using Kubuntu Hardy and my kernel version is 2.6.24-19-generic.

---

