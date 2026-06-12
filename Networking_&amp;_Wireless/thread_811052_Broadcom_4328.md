---
title: "Broadcom 4328"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by ddrlord on 2008-05-28
I have an HP dv6000 with a BCM4328 802.11a/b/g/n wireless card and Hardy Heron installed. I've got it running with ndiswrapper (1.53, I think,) and it works great with an unsecured network. Since I live in a college town, WPA is essentially a minimum. When I try to connect to my network with WPA enabled, NetworkManager asks me for the key, works away in the background for about a minute (with no lights in the tray icon) and then asks again, on loop. I tried Wicd and Wifi-Radar, both of which failed to get IP addresses. When I run dhclient myself, it says "DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval somethingorother" over and over until it just fails. When I try and connect manually, using wpa_supplicant, I get the following on loop:
```
Trying to associate with 00:1c:b3:ad:53:85 (SSID='alswifi' freq=2447 MHz)
Associated with 00:1c:b3:ad:53:85
Associated with 00:1c:b3:ad:53:85
Authentication with 00:1c:b3:ad:53:85 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```
When run with wpa_gui on, I get the following, no less cryptic to me, error:
```
Trying to associate with 00:1c:b3:ad:53:85 (SSID='alswifi' freq=2447 MHz)
ioctl[SIOCGIFADDR]: Cannot assign requested address
Associated with 00:1c:b3:ad:53:85
Associated with 00:1c:b3:ad:53:85
ioctl[SIOCGIFADDR]: Cannot assign requested address
Associated with 00:1c:b3:ad:53:85
ioctl[SIOCGIFADDR]: Cannot assign requested address
Authentication with 00:1c:b3:ad:53:85 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```
And finally, my configuration looks like this:
```
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="alswifi"
        psk="mypasswordhere"
  }
```
I have tried it in many, many varieties, with my psk in quotes, after being run through some program in the terminal, translated into 7 languages, backwards. I've had lines about WPA and fastauth and nothing seemed to make a difference.
Anyone have any advice?

---

