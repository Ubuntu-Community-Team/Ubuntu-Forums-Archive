---
title: "Unplugging wireless USB causes USB issues"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Malbert on 2007-12-19
I've got my Netgear WG111T wireless usb stick working under ndiswrapper however it seems to still be particularly problematic. It works from bootup or works after booting if I plug it in. As soon as I unplug it and plug it back in... or ANY usb device, it doesn't get picked up

DMESG output

[   18.924000] ndiswrapper: driver netwg11t (NETGEAR,09/05/2005,1.5.0.2102) loaded
[   18.924000] ndiswrapper (ZwQueryValueKey:2379): not fully implemented (yet)
[   19.572000] wlan0: ethernet device 00:0f:b5:9d:d9:4f using NDIS driver: netwg11t, version: 0x10005, NDIS version: 0x501, vendor: '', 1385:4251.F.conf
[   19.632000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.632000] usbcore: registered new interface driver ndiswrapper
[   41.228000] wlan0: no IPv6 routers present
[ 3391.176000] usb 5-8: USB disconnect, address 3

address 3 was the wireless stick. After unplugging that I unplugged my mouse and plugged it back in. Failed to be detected either time. 

Does unplugging wireless usb cause ndiswrapper to spud in? Is that what's causing my entire usb system to stop detecting things being removed/plugged in?

Are there any commands I can try to re-initialize usb so I can stop using the damn touchpad?

Cheers

---

