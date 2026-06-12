---
title: "ubuntu server wifi to LAN, no NAT"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by atux on 2015-11-09
hello everyone.
i do have an installation of ubuntu server 12.04 in a PC and it has 3 ethernet ports (eth0, 1, 2) and a usb wifi stick (wlan0).
at the moment the system acts as a NAT server and it has the wlan0 as the wan interface for eth0.
i am connecting to a wifi network with SSID xyz and PASSWD xyz456, wpa2. the network is 192.168.0.0/24, gw 192.168.0.1, and i am getting assigned the 192.168.0.49
current /etc/network/interfaces

  allow-hotplug eth0
auto eth0
iface eth0 inet static
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
   
  auto wlan0
allow-hotplug wlan0
iface wlan0 inet static
  address 192.168.0.49
network 192.168.0.0
netmask 255.255.255.0
  gateway 192.168.0.1
broadcast 192.168.1.255
   
   
  and then
   # echo 1 > /proc/sys/net/ipv4/ip_forward
# iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
# iptables -A FORWARD -i eth0 -j ACCEPT
# iptables -A FORWARD -i wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
  i would like to alter the config a bit and have it connect to the  same network and without any NAT involved and eth0,1,2 be in the same  LAN as the wifi network 192.168.0.0/24
  could someone help me please?
  i have created a clean install to avoid any errors.

---

