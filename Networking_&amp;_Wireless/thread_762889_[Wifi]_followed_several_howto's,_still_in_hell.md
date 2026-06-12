---
title: "[Wifi] followed several howto's, still in hell"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by backupdevice on 2008-04-22
Hi

I need your help

RT2500 based linksys card.Ubuntu 7.10

Followed the howto's available for nsdiswrapper and without ndiswrapper. Used the serialmonk methode. No internet.

I want static ip and wpa-psk.

When i use manual config with NM, i get inet, but after 10 minutes its very slow. I found out that this was a problem with the drivers of the rt2500 card. 

I compiled the serialmonk drivers, blacklisted rt2500pci. So far so go. When i go to networktools and select wlan0, i can see it gets an ip. 

When i do iwconfig i see the AP of my neighbours.
When i do iwlist scan i see my neighbours AP and mine. 

/etc/network/interfaces looks like this 

iface wlan0
address 192.168.1.40
netmask 255.255.255.0
gateway 192.168.1.130
dns-nameservers 213.51.144.37
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

wpa-conf like this

network {
ssid="oebidoebi"
proto=WPA RSN
key_mgmt=WPA-PSK
pairwise=TKIP 
group=TKIP 
psk=hexcode van wpa_passphrase

I've been trying since last friday with 7.10, 8.04 and Mint linux. No luck

---

