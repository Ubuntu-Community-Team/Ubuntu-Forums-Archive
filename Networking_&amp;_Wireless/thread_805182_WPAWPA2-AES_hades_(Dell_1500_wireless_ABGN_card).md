---
title: "WPA/WPA2-AES hades (Dell 1500 wireless ABGN card)"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by yasha on 2008-05-23
Ndiswrapper driver installed
Networks available and connectible for Open, and WEP security enabled.
Wicd used in place of network manager.

In short everything works except WPA encrypted networks. I've tried damn near every variant for the config file I could think of with no luck, it just hangs at getting an IP.

At first I thought this an issue with wicd, but it looks more like an wpa_supplicant issue.

It associates but hangs at getting an IP, then eventually times out. Attached is the output from manually using wpa_supplicant to connect.

I would have just figured Ndiswrapper didn't support WPA2 with AES, but the output of dmesg says otherwise:

[   24.332427] wlan0: ethernet device 00:19:7d:31:04:5c using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   24.332486] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   59.420155] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by yasha on 2008-05-24
Ah well. Between this, it not being able to do 5ghz networking (stuck at 130 rate max) even if I could get WPA2 functional, the laptop overheating due to 7900gs go nvidia driver not controlling the fan(s) including the CPU...Back to windoze XP. Here's hoping for better luck with the release after hardy.

If we could just get decent driver support from the manufacturers linux would be the standard rather than the geek with too much time on their hands option for desktops/laptops.

---

