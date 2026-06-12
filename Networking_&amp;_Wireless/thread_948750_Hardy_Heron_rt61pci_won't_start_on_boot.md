---
title: "Hardy Heron rt61pci won't start on boot"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by bombcar on 2008-10-15
I have Hardy Heron 8.04 and a RaLink RT2561/RT61 802.11g PCI wireless card on a WPA2 network. If I configure it in Network Manager it works fine; until I reboot. Then I have to fiddle with it and turn it off and on and into promiscuous mode and back off before I can bring it up. Any idea on how I can get it to start at boot correctly?

My /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp




iface wlan0 inet dhcp
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid NETGEAR-2.4-G

auto wlan0

```

---

