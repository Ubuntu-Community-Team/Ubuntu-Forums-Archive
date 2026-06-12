---
title: "Wireless Problem"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by trantloveazuen on 2008-11-02
I've a Intel Pro 2200 BG Wireless Card and instaled Wicd in order to conect to my private wireless conection, its a WPA-PSK Network and i can connect to it in windows just fine but not in  ubuntu : / since WICD can't connect to the network ( it hangs on getting IP info ) i decided to configure wpa_supplicant :

###############################################

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
ssid="TranTNetwork"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk="password123"
}
###############################################


in order to conect i do:
1- sudo iwconfig eth1 essid TranTNetwork
2- sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -B
3- dhclient eth1

and in 3 after some line i get :

No DHCPOFFERS received.

what can i do to fix this?

Regards

---

### Post by melojo on 2008-11-02
type this in a console to view available networks

```
iwlist scan
```

see if you can list networks

---

