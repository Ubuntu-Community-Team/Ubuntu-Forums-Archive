---
title: "dhclient causing wpa_supplicant disconnect"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Fergle on 2008-08-20
I'm using a wg111v3 and ndiswrapper to connect to a WPA network.

When dhclient runs, it disconnects wpa_supplicant (CTRL-EVENT-DISCONNECTED is received). 

First start wpa_supplicant:
```

$ wpa_supplicant -Dwext -iwlan0 -c wpa_supplicant.conf

```
Output:
```

Trying to associate with 00:1c:26:36:3b:84 (SSID='Livebox-B5C0' freq=2412 MHz)
Associated with 00:1c:26:36:3b:84
WPA: Key negotiation completed with 00:1c:26:36:3b:84 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1c:26:36:3b:84 completed (auth) [id=0 id_str=]

```

Now run dhclient:
```
$ dhclient wlan0
```

Output:
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:2a:45:38:0d
Sending on   LPF/wlan0/00:1e:2a:45:38:0d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.27 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.27 from 192.168.1.1
bound to 192.168.1.27 -- renewal in 36088 seconds.

```

wpa_supplicant then outputs:
```

CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:1c:26:36:3b:84 (SSID='Livebox-B5C0' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.

```

Then repeatedly times out. After a few goes it will re-associate correctly at which point network behaves correctly (can ping gateway etc). Running dhclient again will repeat the process (ie, wpa_supplicant will disconnect from wireless network).

wpa_supplicant.conf contains:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

### Associate with any open access point
### Scans/ESSID changes can be done with wpa_cli
network={
ssid="Livebox-B5C0"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
psk="<passphase>"
}

```

Anybody seen this before? Any ideas what is causing the problem?

Cheers :)

---

### Post by Fergle on 2008-08-27
*bump*

---

### Post by salemboot on 2008-09-09
My problems ended up being 'wpakey'  its a program that shipped with madwifi.

I turned on wpa encryption and it authenticated.

---

### Post by stooshbunutu on 2008-12-09
you should mark your thread as solved from the thread tools menu

---

