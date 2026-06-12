---
title: "Multiple interfaces in same network"
date: 2014-10-09
forum: Networking &amp; Wireless
---

### Post by demontager on 2014-10-09
I have an Ubuntu server 14.04 without GUI, so using /etc/network/interfaces to setup net. Box has 3 network interfaces - p4p1, wlan0, eth0
My aim is to create so called bridged network with wlan0 and eth0. p4p1 connected to ISP via WAN, wlan0 used as hotspot(hostapd) and eth0 is another USB Lan dongle for wired network. 
```

auto lo br0
iface lo inet loopback

#Wi-Fi-static
auto wlan0
iface wlan0 inet static
address 192.168.1.1
netmask 255.255.255.0


#Lan-Bridge
#iface br0 inet static
#bridge_ports wlan0 eth0
#address 192.168.1.3
#netmask 255.255.255.0
#network 192.168.1.0 

#WAN
auto p4p1
iface p4p1 inet dhcp



```
I have setup Internet connection sharing in iptables and enabled packets forwarding:
```

iptables -A FORWARD -j ACCEPT
iptables -t nat -A POSTROUTING -j MASQUERADE

```
For DNS and DHCP used dnsmasq
```

interface=wlan0
bind-interfaces
dhcp-range=192.168.1.5,192.168.1.240,12h

```
As you may see i commented lines where tried to setup bridge with wlan0 and eth0, but it doesn't work and i lost wifi connectivity.

---

