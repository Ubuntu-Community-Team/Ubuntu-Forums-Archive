---
title: "share internet connection witout GUI"
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by atux on 2016-10-02
hi. in my office i have a place in the warehouse that i cannot have a cable and i need access to the office's router.
in that place i have an ubuntu 12.04 server (no GUI) with an ethernet (eth0) attached to the switch of the warehouse and a USB wifi that connects to the main office's router. currently i am doing a NAT and all the PCs in the warehouse get a different IP from the PCs in the office.
all i need is to share the connection from the wlan0 to eth0 (no NAT) and then all the PCs in the warehouse will IPs from the main office's router.
i have the following:
[COLOR=#000000][FONT=Verdana]/etc/network/interfaces:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auto wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]iface wlan0 inet dhcp[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]wpa-ssid "CommunityWiFi"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]wpa-psk "xyzPaSswD"[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]auto eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]iface eth0 inet dhcp

[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]auto br0[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]iface br0 inet dhcp[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]bridge_ports wlan0 eth0

Any ideas how to make it work please?

[/FONT][/COLOR]

---

### Post by praseodym on 2016-10-03
First, run:

```
sudo apt-get install dnsmasq-base dnsmasq
sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf.bak 
```
Then follow the instructions for "LAN on WLAN" or "WLAN on LAN" (whatever you need) here (German page):

[https://wiki.ubuntuusers.de/Internetverbindungsfreigabe/#Automatische-Konfiguration-DHCP](https://wiki.ubuntuusers.de/Internetverbindungsfreigabe/#Automatische-Konfiguration-DHCP).

Or use the script in the chapter "Instant ICS" there. The script needs to be adapted to your needs.

---

