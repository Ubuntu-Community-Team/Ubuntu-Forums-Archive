---
title: "Feisty + ndiswrapper + WPA2 + Netgear WG111v2"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by LordChaos73 on 2007-05-06
Hi all,

I've got my wireless connection working in Feisty, but strangely enough I have to manually kill wpa_supplicant and restart networking after every reboot. This setup worked flawlessly under Fedora.

The hardware:

- Netgear WG111v2 (rtl8187)

I blacklisted the rtl8187 driver in /etc/modprobe.d/blacklist:

```
# ndiswrapper
blacklist rtl8187
```

I added ndiswrapper to  /etc/modules:

```
ndiswrapper
```

I created /etc/wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=2
fast_reauth=1

network={
       ssid="xxxxx"
       scan_ssid=1
       proto=RSN WPA
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=xxxxxxxxxx
}

```

I modified the wlan0 entries in /etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

I disabled NetworkManager & NetworkManagerDispatcher completely. Everything works fine, but after every reboot I have to manually kill wpa_supplicant and restart the networking service.
Seems like a bug somewhere, but I'm still not sure which component fails. Any ideas ?

---

### Post by LordChaos73 on 2007-05-12
Bump

---

### Post by LordChaos73 on 2007-05-14
I filed this behaviour as a bug:

[https://bugs.launchpad.net/ubuntu/+bug/114310](https://bugs.launchpad.net/ubuntu/+bug/114310)

---

