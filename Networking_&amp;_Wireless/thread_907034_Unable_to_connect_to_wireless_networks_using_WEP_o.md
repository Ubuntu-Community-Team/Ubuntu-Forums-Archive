---
title: "Unable to connect to wireless networks using WEP or WPA"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by necromantula on 2008-09-01
I have a Toshiba laptop with an internal rtl8187B usb wireless adaptor, and i'm using the modified linux drivers for it, on ubuntu 8.04.1.
I can connect to my home wireless when I turn off wireless encryption, but I am completely unable to connect using WEP or WPA.
I have tried multiple methods, involving both wpa_supplicant's config files, and manually editing /etc/network/interfaces.
When I connect to a wireless using WPA or WEP, I think it connects, but when I try to get a dhcp address (using dhclient) I get 
```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6

```
and then some errors saying it basically gives up.
Can anyone help me? I'm hoping to get it working with WPA2, but I would be happy just using WPA. I have a D-Link DGL-4300 router, configured to allow both WPA and WPA2 at the same time, using a shared ascii key.

---

