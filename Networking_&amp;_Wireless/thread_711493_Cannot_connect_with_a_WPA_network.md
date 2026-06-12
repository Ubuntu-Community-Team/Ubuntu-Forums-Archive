---
title: "Cannot connect with a WPA network"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by ronniegaucho on 2008-02-29
Hello,

I've just installed in my home a router protected by a WPA key, but Ubuntu isn't able to connect with.

I've created a file (/etc/wpa_supplicant) which has the following content:

```

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1

network={
      ssid="votre_ssid"
      proto=WPA RSN
      key_mgmt=WPA-PSK
      psk="votre_clé_en_clair"
}

```

When I tape:

```

$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -w -Dipw -iwlan0

```

(Because the network PCI card is an Intel Corpoation PRO/Wirless 2200 BG)

But it returens me:

```

ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
```

Czn you help me please? Thanks

---

### Post by Cenotaph on 2008-02-29
type iwconfig and see which is your device, it might not be wlan0 but eth1 or eth0, i'd also suggest you try to use -Dwext for a generic device instead of -Dipw

---

