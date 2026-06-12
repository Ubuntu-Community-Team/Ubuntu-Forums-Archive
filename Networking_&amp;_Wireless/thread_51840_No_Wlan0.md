---
title: "No Wlan0"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by umdzig on 2005-07-25
Im new to linux. I have used Knoopix and my wireless works great with the help of ndiswrapper. However, I cant use my wireless in Ubuntu. In network settings the Wlan0 does not show up. In network tools the only network connections i have is loopback and my ehternet interface. When i go to root and type iwconfig it says no wireless extensions. When i go to device manager it knows the wireless card is there but just says unknown for capabilities. Any help is appreciated.

---

### Post by umdzig on 2005-07-25
k i figured out i had messed up the ndiswrapper installation. I can now see the Wlan0, however i can not see any ap when i type iwlist scan. I think i need to change the channel its on 11 right now and my ap is on 4. How do i change it from channel 11 to 4? thx

---

### Post by umdzig on 2005-07-25
k my card will not pick up on any ap. when i type iwlist scan it says no scan results. When i type ifup wlan0 i get:

root@laptopmike:/home/zig # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:50:4e:23:4e:e4
Sending on   LPF/wlan0/00:50:4e:23:4e:e4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

NEED HELP

---

### Post by ychen on 2005-07-26
Firstly, use "lspci" or "lsusb" to see which card you have.
Then find a module to load or use the "ndiswrapper".

---

