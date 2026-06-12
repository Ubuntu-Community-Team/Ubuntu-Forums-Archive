---
title: "how to set dhcpd.config file about the address"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by ryan43 on 2014-01-22
I tried to used hostapd and dhcp service to build a hotspot on my ubuntu laptop, I have already get a hostapd.config file, then according to the method I found I should add the comment:

subnet  192.168.0.0  netmask   255.255.255.0

{

range   192.168.0.2    192.168.0.10;

option   routers   192.168.0.1;

option   domain-name-servers   8.8.8.8;   

}
into the /etc/dhcp/dhcpd.config fileand then I get a scrip:

#!/bin/bash
#this is ap create script 

sudo   ifconfig    wlan0   192.168.0.1       netmask     255.255.255.0
sudo   dhcpd      wlan0     -pf        /var/run/dhcp-server/dhcpd.pid
sudo   bash         -c     "echo       1    >        /proc/sys/net/ipv4/ip_forward"
sudo   iptables    -t      nat    -A    POSTROUTING     -o   eth0     -j   MASQUERADE
sudo   hostapd     /etc/hostapd/hostapd.conf   &

all these I get from the internet, so I am not quite sure wthether I can use the address like that or I should use my own
the information about relevent address is:
[ATTACH=CONFIG]249661[/ATTACH]
so how can I change the address into the right one? Thank very much

---

