---
title: "WiFi Dropping Connection"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by runt on 2008-03-28
Ok,
My WiFi (RTL8187B using ndiswrapper) was working great earlier today.  I upgraded to 8.04 Beta and it worked for an hour after that.  Now I can connect to the AP, get an IP address (AP is a Linksys WRT-54G running DD-WRT firmware and the DHCP server is a Clarkconnect box) but I can only access the 'Net if I boot into the recovery console.  This happened last night and all I had to do was reboot the AP.  I tried that tonight and it didn't fix anything.  I don't really want to have to re-install 7.10 just because the 8.04 Beta upgrade broke something.

I run WPA-PSK and here is my wpa_supplicant.conf file
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="runt"
    scan_ssid=0
    proto=WPA
    key_mgmt=WPA-PSK
    psk=72073e9b17235377a4ce53ac74d0059082b7d3815fa062c1f9f2bc9a0284aaef
    pairwise=TKIP
    group=TKIP
}

network={
    ssid="lakeview"
    scan_ssid=0
    proto=WPA
    key_mgmt=WPA-PSK
    psk=9432baa6a649fc096294196b0343c7a4a78958b970412d120259e8c83de01970
    pairwise=TKIP
    group=TKIP
}
```

and here is my /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf
```

---

### Post by pHreaksYcle on 2008-03-29
[http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-beta-review-and.html](http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-beta-review-and.html)

This is most likely your issue, as has been with everyone else I know with your symptoms.

---

### Post by runt on 2008-03-29
> **pHreaksYcle said:**
> [http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-beta-review-and.html](http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-beta-review-and.html)

This is most likely your issue, as has been with everyone else I know with your symptoms.

Unfortunately, that did not fix the issue.  I know the wireless works in the apartment because my fiance can connect to it.

I can authenticate if I run ```
sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w
``` but I get a ```
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
``` around once every 10 seconds.  I am thinking I will have to reinstall 7.10 for now and not upgrade to 8.04 until it is officiall released (which sucks since I have my system setup the exact way I want it).

---

