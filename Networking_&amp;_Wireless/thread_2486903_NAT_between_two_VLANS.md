---
title: "NAT between two VLANS"
date: 2023-05-16
forum: Networking &amp; Wireless
---

### Post by NachoMas on 2023-05-16
Hi all,

I have an special setup to connect my internal home network to the internet that I am not able to sort out. Just now I'm using a WLAN router and I want to move my NATting + DHCP server to an ubuntu server with one single interface. I have create to VLANs in my switch and configured the eth interface in my server with two VLANs (wan_vlan@eno1 and lan_vlan@eno1) and I have configured the kea dhcpd server to listen on the physical interface (eno1) and answer the requests for the lan VLAN subnet (192.168.1.0/24) (that was as well a bit of complicated, since it does not work if you do not put an IP address on the eno1 interface itself). The wan vlan interface (wan_vlan@eno1) receives an IP address from my CSP and from my ubuntu server I'm able to ping the world from the server router, but I don't manage to configure NAT in the router to ping the outside world from my LAN network nodes. This is the way I'm trying to configure the NAT:

Contents of rc.local in the router:

#!/bin/bash

# Accept input packet if the router initiated the connection
iptables -A INPUT -i wan_vlan@eno1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# Forward LAN packets to the WAN.
iptables -A FORWARD -i lan_vlan@eno1 -o wan_vlan@eno1 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i wan_vlan@eno1 -o lan_vlan@eno1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o wan_vlan@eno1 -j MASQUERADE


iptables -A INPUT -i wan_vlan@eno1 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -i wan_vlan@eno1 -p tcp --dport 443 -j ACCEPT

iptables -A INPUT -i wan_vlan@eno1 -p icmp -j ACCEPT

iptables -A INPUT -i wan_vlan@eno1 -j DROP

# rc.local needs to exit with 0
exit 0
-----------------

So, is there something that I'm obviously doing wrong in the way I'm trying the NAT between the two VLANs? Does NAT work with vlan tagged traffic at all?

Thanks!
/Nacho

---

