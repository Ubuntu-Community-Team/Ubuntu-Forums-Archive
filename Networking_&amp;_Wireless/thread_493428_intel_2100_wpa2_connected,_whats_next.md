---
title: "intel 2100 wpa2 connected, whats next?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by houms on 2007-07-05
I recently installed Feisty Fawn, and finally got the wireless connection working. Using WPA2 encryption, with a hidden SSID.... The only configuration I did after install was with creating and configuring /etc/wpa_supplicant.conf.

The connection is great, but I want to assign a static ip address to my wireless interface(eth1). I have read posts and tried to modify /etc/network/interfaces, but cannot get it to connect. If I leave the default configuration file, like below everything works.

 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


but if I modify to receive a static ip like below, I cannont get it to connect

auth eth1
iface eth1 inet static
address 192.168.0.20
gateway 192.168.0.1
dns-nameservers 192.168.0.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid myssid
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk myhexkey 

Any help would be appreciated

---

