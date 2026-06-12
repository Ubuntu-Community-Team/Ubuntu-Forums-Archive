---
title: "WUSB54Gv1 ... why doesn't it work? (with WPA)"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Atreus12 on 2007-05-31
I am getting a bit frustrated with feisty as I can't get WPA to work with my wusb54gv1.

I had everything working perfectly in 6.06, WPA worked, it automatically connected at bootup.

I even had it working in DSL (damnsmalllinux) with WPA.

After a number of hours (not exaggerating) of trying everything I can think of in Feisty...it just doesn't work with WPA. It's interesting that as the version number goes up, the wireless ability goes down. :(

If anyone has any suggestions, I would love to hear them. I copied by /etc/network/interfaces file directly from 6.06


/etc/network/interfaces
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
#wpa-conf managed (commented out after reading sticky in networking forum)
wpa-ssid ubuntu
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 7825aec1be9f0...and so on

```

after running /etc/init.d/networking restart
```

user@box:~$ sudo /etc/init.d/networking restart
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:fb:87:80
Sending on   LPF/wlan0/00:0c:41:fb:87:80
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:fb:87:80
Sending on   LPF/wlan0/00:0c:41:fb:87:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```



EDIT: RESOLVED

Installed Debian Etch, works perfectly.
[Guide](http://www.debian-administration.org/articles/401)

---

