---
title: "My connection keeps dropping out"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by c0rrupt on 2007-05-18
This never happens in Windows XP.  Can someone tell me what is going on here?  Whenever this happens I just have to Ctrl-C wpa_supplicant and run it again.  Network-manager will reconnect for me automatically but I'm getting tired of having my connection drop out so much no matter what I try.

Edgy Eft
Edimax EW-7325IG w/ Atheros AR5212 Chipset (according to Gnome device manager)

Oh, I'm not using ndiswrapper or anything.  Just the drivers that came with edgy.

```

david@ax78e4:~$ sudo wpa_supplicant -Dmadwifi -iath0 -c /etc/wpasupplicant.conf
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
WPA: Key negotiation completed with 00:XX:XX:XX:XX:XX [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:XX:XX:XX:XX:XX completed (auth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
WPA: Key negotiation completed with 00:XX:XX:XX:XX:XX [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:XX:XX:XX:XX:XX completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:XX:XX:XX:XX:XX (SSID='MYNETWORK' freq=2452 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:XX:XX:XX:XX:XX
WPA: Key negotiation completed with 00:XX:XX:XX:XX:XX [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:XX:XX:XX:XX:XX completed (reauth) [id=0 id_str=]
WPA: EAPOL-Key Replay Counter did not increase - dropping packet

```

---

### Post by handaxe on 2007-05-21
of help (or further frustration ...)?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821)

HA

---

