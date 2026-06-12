---
title: "SAMBA and iptables FORWARD rules"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by SlowRedFox on 2007-08-25
I have set up an old computer running ubuntu as a multi-purpose server and wired/wireless router. I would like to use SAMBA to share files with windows users on the network - and everything works perfectly. 
However, the firewall script that I'm using is modified from one I found in a magazine, which drops all forwarded packets by default: 
 
```
 
#!/bin/sh 
# list of variables 
WAN_IF=ppp0 
LAN_IF=eth0 
WLAN_IF=ath0 
LAN_NET=192.168.0.0/24 
WLAN_NET=192.168.1.0/24 
 
# default chain policies 
iptables -P INPUT DROP 
iptables -P FORWARD DROP 
iptables -P OUTPUT ACCEPT 
iptables -F 
 
# allow localhost traffic 
iptables -A INPUT -i lo -j ACCEPT 
# allow LAN traffic 
iptables -A INPUT -i $LAN_IF -j ACCEPT 
# allow WLAN traffic 
iptables -A INPUT -i $WLAN_IF -j ACCEPT 
# allow outgoing traffic from LAN 
iptables -A FORWARD -o $WAN_IF -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu 
iptables -A FORWARD -i $LAN_IF -s $LAN_NET -o $WAN_IF -j ACCEPT 
iptables -A FORWARD -i $WLAN_IF -s $WLAN_NET -o $WAN_IF -j ACCEPT 
# allow return packets from internet to router/LAN 
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -i $WAN_IF -m state --state RELATED,ESTABLISHED -j ACCEPT 
 
# enable NAT for LAN traffic 
iptables -t nat -A POSTROUTING -o $WAN_IF -j MASQUERADE 
 
# enable ping 
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT 
iptables -A INPUT  -p icmp --icmp-type echo-reply   -j ACCEPT 
iptables -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT 
iptables -A FORWARD -p icmp --icmp-type echo-reply -j ACCEPT 
iptables -A INPUT -p tcp --syn -m limit --limit 5/s -i eth0 -j ACCEPT 
 
# open samba ports to network 
iptables -A INPUT -p udp -m udp -s 192.168.0.0/24 --dport 137 -j ACCEPT 
iptables -A INPUT -p udp -m udp -s 192.168.0.0/24 --dport 138 -j ACCEPT 
iptables -A INPUT -m state --state NEW -m tcp -p tcp -s 192.168.0.0/24 --dport 139 -j ACCEPT 
iptables -A INPUT -m state --state NEW -m tcp -p tcp -s 192.168.0.0/24 --dport 445 -j ACCEPT 
iptables -A INPUT -p udp -m udp -s 192.168.0.0/24 --dport 137 -j ACCEPT 
iptables -A INPUT -p udp -m udp -s 192.168.0.0/24 --dport 138 -j ACCEPT 
iptables -A INPUT -m state --state NEW -m tcp -p tcp -s 192.168.1.0/24 --dport 139 -j ACCEPT 
iptables -A INPUT -m state --state NEW -m tcp -p tcp -s 192.168.1.0/24 --dport 445 -j ACCEPT 
 
# opening ports 
iptables -A INPUT -i $WAN_IF -p tcp --dport 22 -j ACCEPT 
iptables -A INPUT -i $WAN_IF -p tcp --dport 6891 -j ACCEPT 
iptables -A INPUT -i $WAN_IF -p udp --dport 6891 -j ACCEPT 
 
# forwarding ports 
iptables -A FORWARD -i $WAN_IF -p tcp -d 192.168.0.10 --dport 6891 -j ACCEPT 
iptables -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 6891 -j DNAT --to 192.168.0.10 

``` 
 
 This stop computers on the network from connecting to each other (though they connect to the server fine). I have it set up with seperate networks for each interface (one for wired and one for wireless). After allowing all packets to be forwarded with: ```
sudo iptables -P FORWARD ACCEPT
``` Then SAMBA works perfectly. 
What rules do I need to add to this script iin order to have the computers connect to each other through SAMBA? And are there any gross security flaws in this script?

---

