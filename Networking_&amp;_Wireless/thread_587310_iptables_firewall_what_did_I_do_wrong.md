---
title: "iptables firewall what did I do wrong ?"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Helbo15 on 2007-10-22
I've partly taken this script from someone else  and edited it 4 my own purpose
 however it did work at my old LFS installation and at my old fedora core2 installation 
I've edited it in between and so far havn't had the biggest troubles with it 

but now I've done somthing with it so it won't work at my ubuntu installation :( 

I hope some of u can see my error cause I've lost track of were and when I edited in it

I allso hope u'll see that I want the security up but not at the expense of my games or surfing ^^; 

And please don't tell  me to use some gui I do this to learn iptables and cause I've heard that it is basically what all the gui programs will create rules with anyway ^^

in advance thanks :)

 ```

#!/bin/sh

# STOP FORWADING
echo "Stopping IP-Tables"
echo 0 > /proc/sys/net/ipv4/ip_forward
sleep 1

## NETWORK INTERFACES
WAN_NIC="eth1"
LAN_NIC="eth0"
LAN_NET="192.168.1.0/24"

## LOAD MODULES
modprobe ip_nat_ftp
modprobe ip_conntrack
modprobe ip_conntrack_ftp
modprobe ip_tables
modprobe iptable_nat
modprobe ipt_MASQUERADE

## FLUSHING / CLEANING UP EARLIER RULES
iptables --delete-chain
iptables -t nat -F POSTROUTING
iptables -t nat -F PREROUTING
iptables -t nat -F OUTPUT
iptables -t nat -F
iptables -F

## RULES
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

## ENABLE FORWARDING
echo 1 > /proc/sys/net/ipv4/ip_forward

## ENABLE MASQUERADE AND FORWARDING.
iptables -t nat -A POSTROUTING -o $WAN_NIC -j MASQUERADE
iptables -A FORWARD -o $LAN_NIC -i $WAN_NIC -j ACCEPT

## ENABLE TCP MSS BECAUSE OF ADSL TCP ICKYNESS
iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

## OPEN TRAFFIC FOR LOOPBACK DEVICE
iptables -A INPUT -i lo -p all -j ACCEPT
iptables -A OUTPUT -o lo -p all -j ACCEPT

## OPEN SERVICES ON ROUTER (INBOUND).
iptables -A INPUT -j ACCEPT -p tcp -m multiport --dport ssh,8080
iptables -A INPUT -j ACCEPT -p udp -m multiport --dport 8767

## ALLOWED OUTGOING PORTS FROM LAN TO WAN.
iptables -A FORWARD -j ACCEPT -p tcp -m multiport --dport 21,22,53,80,110,143,443,1863,3724,6112,1188,8080
iptables -A FORWARD -j ACCEPT -p udp -m multiport --dport 21,22,53,80,110,143,443,1863,3724,6112,1188

## ALLOWED PORTS FROM THE ROUTER TO WAN.
iptables -A OUTPUT -j ACCEPT -p tcp -m multiport --dport 53,80
iptables -A OUTPUT -j ACCEPT -p udp -m multiport --dport 53,80

## ALLOW DHCP REQUEST
iptables -I INPUT -i $LAN_NIC -p udp --dport 67:68 --sport  67:68 -j ACCEPT

## ALLOW RANGE // BITTORRENT
iptables -A FORWARD -j ACCEPT -p tcp --dport 6881:6999

## NAT PORTS TO SERVER
##iptables -A FORWARD -j ACCEPT -p tcp -m multiport --dport 21,22,25,53,80,110,143,3724,6112
##iptables -t nat -A PREROUTING -i $WAN_NIC -p tcp -m multiport --dport 21,22,25,53,80,110,143 -j DNAT --to 192.168.1.2

#WEB NAT
##iptables -t nat -A PREROUTING -i $WAN_NIC -p tcp --dport 80 -j DNAT --to 192.168.1.1
##iptables -t nat -A PREROUTING -i $WAN_NIC -p tcp --dport 6881:6999 -j DNAT --to 192.168.1.1

##iptables -t nat -A POSTROUTING -d 192.168.1.1 -s 192.168.1.0/24 -p tcp --dport 80 -j SNAT --to 192.168.1.1

## ALLOW SAMBA REQUEST ON LAN_NIC
## iptables -A INPUT -i $LAN_NIC -p tcp -m multiport --dport 137,138,139,445 -j ACCEPT
## iptables -A INPUT -i $LAN_NIC -p udp -m multiport --dport 137,138,139,445 -j ACCEPT

## ACCEPT ESTABLISHED CONNECTIONS
iptables -A INPUT -i $WAN_NIC -m state --state ESTABLISHED,RELATED -j ACCEPT

## ALLOW ABOVE-MENTIONED TRAFFIC TO PASS
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

echo "Starting IP-Tables"

```

---

### Post by Helbo15 on 2007-10-23
can't any help me ^^;

---

### Post by Helbo15 on 2007-10-24
are it really that hard ^^;

---

