---
title: "Complex UDP Multicast Routing"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by cdorsey on 2016-11-11
I'm using an ubuntu system as a router, following [this guide]("https://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/") with some minor modifications to the dnsmasq.conf file to use the 172.16.X.X subnet for assigning IP addresses via DHCP. A windows system is connected to the ubuntu "router" via eth0, and is sending UDP multicast packets out. By running "ip route add 224.0.0.0/4 dev eth0" and "ip maddr add 239.252.101.255 dev eth0", I can view the incoming UDP traffic through "tcpdump -p udp." Now, another windows system connects to the ubuntu "router" via wlan1 to listen to the multicast traffic. After opening up wireshark, to my surprise, no UDP multicast traffic is captured. Please note, if I connect both of the windows systems together over ethernet, I can see all UDP traffic. 

**What am I missing?**

Below is a sample of how my system is setup and my version of the initSoftAP script from the guide above.

_Setup: _

windows system 1 |172.16.101.1| <- eth0 -> |172.16.3.1| ubuntu "router" |172.16.4.1| <- wlan1 -> |172.16.4.101| windows system 

_Script: _

#!/bin/bash
#Initial wifi interface configuration
ifconfig $1 up 172.16.4.1 netmask 255.255.0.0
sleep 2
 
#Start dnsmasq
if [ -z "$(ps -e | grep dnsmasq)" ]
then
 dnsmasq
fi
 
#Enable NAT
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface $2 -j MASQUERADE
iptables --append FORWARD --in-interface $1 -j ACCEPT
 
sysctl -w net.ipv4.ip_forward=1
 
#start hostapd
hostapd /etc/hostapd/hostapd.conf
killall dnsmasq

---

