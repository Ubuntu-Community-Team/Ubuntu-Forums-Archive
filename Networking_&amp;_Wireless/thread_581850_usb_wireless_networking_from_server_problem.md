---
title: "usb wireless networking from server problem"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by jimisdead on 2007-10-19
I have an old laptop that I use as a file/printer/everything server, that is currently connected via ethernet by a large ugly cable trailled through my apartment.

I want to change it to use a spare netgear wireless usb card, which after updating to gutsy I now see is supported - and is automatically shown as wlan0 when plugged in.

without further ado here is my /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        dns-nameservers 192.168.2.1

        gateway 192.168.2.1

auto wlan0
iface wlan0 inet static
        address 192.168.2.10
        gateway 192.168.2.1
        dns-nameservers 192.168.2.1
        netmask 255.255.255.0
        wpa-driver wext
        wpa-ssid MYNETWORKSSID
        wpa-ap-scan 1
        wpa-proto RSN
        wpa-pairwise CCMP
        wpa-group CCMP
        wpa-key-mgmt WPA-PSK
        wpa-psk MYNETWORKKEYKEYKEY



```

if I boot this this config I can ping and ssh into either 192.168.2.2 or 192.168.2.10 and everything is great. If I then unplug the ethernet cable I can not ping 192.168.2.2 anymore (obviously), but nor can I ping 192.168.2.10 - and I can't get any network connection from the serverside either..

... Does anyone have any idea what is going on?

---

