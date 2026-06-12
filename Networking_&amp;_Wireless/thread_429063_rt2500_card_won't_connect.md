---
title: "rt2500 card won't connect"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Pas3n7 on 2007-04-30
I'm using this script

/etc/dbus-1/event.d/26NetworkManagerDispatcher stop
/etc/dbus-1/event.d/25NetworkManager stop
ifconfig eth0 down
ifconfig ra0 up
iwconfig ra0 essid "myssid"
iwconfig ra0 mode managed
iwconfig ra0 channel auto

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwpriv ra0 set WPAPSK="puppyface"
iwpriv ra0 set TxRate=0
iwconfig ra0 essid "myssid"

I've (obviously) changed the ssid and wpa key.

When I run this all appears well, but I can't it won't get an ip through dhcp, and if I assign it an ip manually, I don't get any ping response.

Any idea what I'm doing wrong?

---

### Post by Austin_KW on 2007-04-30
If it is 7.04, try setting the ssid when the ra0 is down.

ifconfig ra0 down
iwconfig ra0 essid "myssid"
... rest...
ifconfig ra0 up (or dhclient ra0)

---

### Post by Pas3n7 on 2007-05-01
Thanks for the quick reply. Unfortunately though, that didn't fix it.

I should probably include a little more information

I'm on 7.04 and I'm using the latest CVS source of the rt2500 drivers (the beta drivers wouldn't compile)
Also it connects fine if I turn encryption completely off. It didn't work with WEP either (though that may have been my fault, I'll try it again a little later).

edit: wep works fine. It appears to be a WPA issue. The router (dd-wrt) is set up to accept WPA 1 and 2 using tkip and aes, so that shouldn't be a problem. any suggestions on how to make WPA work?

---

### Post by Austin_KW on 2007-05-01
Try setting the router to just use WPA1 and tkip.

---

### Post by Pas3n7 on 2007-05-01
Same result.

---

