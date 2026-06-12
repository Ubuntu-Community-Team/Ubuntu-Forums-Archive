---
title: "Gui for starting wifi connection"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by fettuohi on 2007-01-07
I have wireless network at home setup securely with wpa-psk (SSID is not broadcasted). Everything is working under Windows of course but I want it to work under linux also (Kubuntu 6.10 with my Netgear WAP511 card). That I have achieved by adding the following lines to /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant 
ctrl_interface_group=root
ap_scan=1
network={
ssid="HyperNetwork"
proto=WPA
scan_ssid=1
key_mgmt=WPA-PSK
# psk="OpenTheDoor"
psk=38144375f57e9bdda07e97ab6a58c3f5cf794fc7d85a83 fca95cc2b7
pairwise=CCMP TKIP
group=CCMP TKIP WEP104 WEP40
priority=2
}

then I set the ip address etc. in /etc/network/interfaces

iface ath0 inet static
address 11.2.3.10
netmask 255.255.255.0
broadcast 11.2.3.255
gateway 11.2.3.1

after that I restart my network and I type in a terminal

wpa_supplicant -i ath0 -c /etc/wpa_supllicant.conf -D madwifi -w -d

and I get the handshake and I have a wifi connection. My question now how can I set this up with a gui like Wifi Radar or knetworkmanager???

With Wifi Radar I don't know how to fill out the lines especially the line saying Wifi --> key and WPA --> Driver? The Knetworkmanager for some reason can't find my card when I start it. Any suggestions or help would be great, thanks.

Regards

André

---

### Post by Treviño on 2007-01-07
Set
ctrl_interface_group=1000

Or replace "1000" with your $USER instead...

---

