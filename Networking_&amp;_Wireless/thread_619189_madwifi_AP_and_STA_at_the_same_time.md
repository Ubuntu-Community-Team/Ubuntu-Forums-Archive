---
title: "madwifi: AP and STA at the same time"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by mauritzius on 2007-11-21
Hello, 

My university requires me to use WPA2/PEAP. I want my Palm to be able to connect to the network as well, but the TX does not support WPA2 without certificates. 

As my Laptop has an integrates Atheros card, I thought about the following setup:

1) Laptop creates VAP (ath1) using WEP or WPA the palm can connect to
2) Laptop connects (ath2) to the university's network using WPA2/PEAP
3) Laptop masquerades ath1/ath2

1) and 2) work seperately as expected, but as soon as wpa_supplicant is started, the AP can't send/receive anymore (and is not visible in scanning from).

Has anyone experience with this? Why does the VAP stop? Is this a madwifi-problem, a wpa_supplicant-problem or a ubuntu-problem?

Here is how my AP is set up (I uninstalled network-manager):

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath1
iface ath1 inet static
pre-up wlanconfig ath1 create wlandev wifi0 wlanmode ap
pre-up wlanconfig ath2 create wlandev wifi0 wlanmode sta nosbeacon
wireless-mode master
address 10.0.0.10
netmask 255.0.0.0
broadcast 10.0.0.255
wireless-essid myap
wireless-key xxxxxxxxxx

auto ath2
iface ath2 inet dhcp
pre-up wpa_supplicant -D madwifi -i ath2 -c /etc/wpa_supplicant/wpa_supplicant.conf -B -w
post-down killall -q wpa_supplicant

iface ppp0 inet ppp
provider ppp0

```

/etc/wpa_supplicant/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
update_config=1
ap_scan=1

network={
        ssid=xxxxxx
        proto=WPA2
        key_mgmt=WPA-EAP
        eap=PEAP
        scan_ssid=1
        identity="xxxxxx"
        password="xxxxxx"
}

```

---

