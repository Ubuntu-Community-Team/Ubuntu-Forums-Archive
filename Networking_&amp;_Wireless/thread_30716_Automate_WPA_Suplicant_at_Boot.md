---
title: "Automate WPA Suplicant at Boot"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by Rob2687 on 2005-04-29
How do I auto mate wpa supplicant at boot?

Right now have to do
```

sudo wpa_supplicant -i wlan0  -c /etc/wpa_supplicant.conf -D ndiswrapper
/sbin/dhclient wlan0

``` 
inorder to get the wpa authentication thing working and dhcp setup.

when I run the first line it shows:
```

Trying to associate with 00:00:00:00:00:00 (SSID='Networky' freq=2422 MHz)
Associated with 00:00:00:00:00:00
WPA: Key negotiation completed with 00:00:00:00:00:00 [PTK=TKIP GTK=TKIP]

```

and I have to leave that terminal open otherwise the connection will be lost....

---

### Post by mat2057 on 2005-04-30
first you can add "-B" to demonize wpa_supplicant.

---

