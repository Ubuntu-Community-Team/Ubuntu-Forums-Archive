---
title: "Coffee Shop Wifi"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by theShogun on 2007-09-28
Trying to get WEP to work on Feisty is killing me. I have installed network-manager-gnome as per [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager), and I have also installed wpa_supplicant. My /etc/network/interfaces is as follows

auto lo
iface lo inet loopback

#iface eth0 inet dhcp
#iface eth1 inet dhcp

I try to connect to the network at the coffee shop using the ESSID and WEP key. It's not working. What do I do if the WEP key is 40/128 hex? Network manager only seems to be able to handle 64/128 (or am I completely wrong on that? I don't know). Otherwise, is there anything that I'm missing to get this up and running?

---

### Post by HermanAB on 2007-09-28
Try WiFi Radar.

Cheers,

Herman

---

