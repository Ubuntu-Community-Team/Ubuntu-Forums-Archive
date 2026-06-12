---
title: "Acer Aspire 3700 Wifi problem"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by shanDB on 2011-01-31
Hi,

It seems that a bunch of people are having the same problem as me, and none of the solutions appear to work for me, so I really hope that someone has resolved this issue.

I'm a bit of a newbie with all of this, so please break down any responses for someone that has had very minimal experience using the command line.

My hardware: Acer Aspire 3700
Running: XBMCLive Dharma 10.0

Problem:
I'm having issues connecting XBMC to my home wifi network.

# I've installed wpasupplicant, and installed drivers for the RT3090, encrypted my pass_phrase with no problems, and also added the following lines to my network/interfaces file (and also commented out the working ethernet connection temporarily):
```
auto wlan0
iface wlan0 inet dhcp
wpa-ssid Wireless Home
wpa-ap-scan 1
wpa-proto WPA #RSN
wpa-pairwise TKIP #CCMP
wpa-group TKIP #CCMP
wpa-key-mgmt WPA-PSK
wpa-psk ffe1b80746215def132a6afa2f192c90f5bed672b5793f17362086a7624ebe9d
```

When I **iwconfig** I get the following:
```
lo - no working extensions

eth0 - no working extensions

wlan - Ralink STA ESSID:""
Mode:Auto Frequency=2.412 Ghz
Link Quality=10/100 Signal levek:0 dbm Noise level:-143 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

But when I **sudo iwlist scan** I get the following:
```
Lo - Interface doesn't support scanning

eth0 - Interface doesn't support scanning

wlan0 - Interface doesn't support scanning : Network is down
```

I'm unsure as how to proceed from here.
It's worth noting that xbmc does work fine with my ethernet cable, but I really want to use it via wifi.

Thanks in advance, and please let me know if I need to supply any additional information.

---

