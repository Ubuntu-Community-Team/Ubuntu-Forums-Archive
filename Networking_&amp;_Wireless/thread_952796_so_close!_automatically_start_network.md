---
title: "so close! automatically start network"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by doorknobandfridgetheory on 2008-10-19
Greetings,

I have just installed Hardy Heron and and actually got my wireless working. The problem is that I have to open System-Admin-Networks and re-enter the network key(WPA) and then run the following 2 commands, after which i can access the internet.

sudo dhcpcp wlan0
sudo ifconfig wlan0 up

and this has to be done everytime I restart. What do I need to do so the network is started during boot?

if it helps, this is the contents of my /etc/networks/interfaces

auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wpa-psk f215c52e3726abf7d435f27185205ad0a70ca66ea4ab8c0c9174c99959b96c28
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid BTHomeHub2-WTZG

auto wlan0

Thank you.

---

