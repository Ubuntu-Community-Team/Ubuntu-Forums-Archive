---
title: "Reboot keeps manual settings but will not connect unless re entered"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by rw_mott on 2008-08-08
Hi,
Each time I reboot my computer the wireless network connection doesn't connect. If I look in network manager it has remembered all the manual settings I'm using but it will not connect unless I go through and re enter the details. I'm trying to set it up with a static IP and WPA protection.

thanks

below are the network card specs:

  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wmaster0
       version: 00
       serial: 00:0c:f6:34:dd:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.166 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

---

### Post by Iowan on 2008-08-08
**/etc/network/interfaces**: Device (wmaster?) has "auto" line (ie. is it automatically activated on reboot)?

---

### Post by rw_mott on 2008-08-08
etc/network/interfaces has no device wmaster0 which I assume is the problem. It has 3 different devices wlan0 1,2 each with a different static IP from which were ones I have tried changing in network manager in case the address was causing the problem, see below.
Can I edit this to make it boot properly? Thanks!

auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.0.167
netmask 255.255.255.0
gateway 192.168.0.1
wpa-psk "my password"
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid "my network"

auto wlan0

iface wlan1 inet static
address 192.168.0.118
netmask 255.255.255.0
gateway 192.168.0.1
wpa-psk "my password"
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid "my network"

auto wlan1

iface wlan2 inet static
address 192.168.0.165
netmask 255.255.255.0
gateway 192.168.0.1
wpa-psk "my password"
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid "my network"

auto wlan2

---

### Post by Iowan on 2008-08-08
> **rw_mott said:**
> Can I edit this to make it boot properly? Thanks!It'd be worth a try...
First, I'd make a backup - from a terminal:```
cp /etc/network/interfaces /etc/network/interfaces.bak
``` If it generates an error - try it with "sudo cp..." After that:```
sudo nano /etc/network/interfaces
```Quick-and-dirty would be to change "wlan0" to "wmaster0".  
One cavaet worth mentioning... I don't have/use/understand wireless yet, so be forewarned.

---

