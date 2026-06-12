---
title: "Define a route via iptables"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by rober2 on 2014-06-11
[COLOR=#000000][FONT=Arial]Hello everyone,

I'm a newbie at ubuntu's administration although I've been using linux for a while just at user level. Let's show my problem.

This is my network (only static IP addresses are used, for both private and public ones):[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]LAN1: 128.100.100.0/24[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]|[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]|[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]|[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]L_____128.100.100.30[/FONT][/COLOR]
         [COLOR=#000000][FONT=Arial]            Router[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]L_____192.168.110.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]|[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]|[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]LAN2: 192.168.110.0/24[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  |[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  |[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  L__ Linux box ubuntu server 14.04 named atlas: 2 Ethernet interfaces[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]          L__ eth0: Internet 193.144.186.15/24 (default gateway is 193.144.186.1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]          L__ eth1: LAN 192.168.110.11/24[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Iptables are used to configure atlas's firewall. All communications between LAN2 and atlas or LAN2 and Internet work out fine. No routes are defined via the route command.
[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The issue is as follows:

A single ping sent from host 128.100.100.1 (remote1) to 192.168.110.11 (atlas's eth1) doesn't work. Actually, the ICMP request correctly arrives atlas's eth1 interface (I checked with wireshark at eth1), but no ICMP reply is sent from atlas to remote1.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]However, if one route is added in atlas, the ping request is correctly replied. Here is the route (informing about which is the router to reach the inner 128.100.100.0 network from atlas):[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]route add -net 128.100.100.0/24 gw 192.168.110.1 dev eth1[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]You may say that, if it works, it all is ok, but my challenge is not to use the *route*command, but to use only iptables rules to make things work between both LANs (128.100.100.0 and 192.168.110.0 network). My iptables rules are based on an example by Oskar Andreasson at [https://www.frozentux.net/iptables-tutorial/scripts/rc.firewall.txt](https://www.frozentux.net/iptables-tutorial/scripts/rc.firewall.txt)

My question is: is it possible to achieve what I want using only iptables? Or is it impossible and Imust use route command?[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Here it is the iptables script executed on boot.

Thank you.
Rober[/FONT][/COLOR]


```

[FONT=courier new]# Reset tables/chains/rules[/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -F[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -X[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -t nat -F[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -t nat -X[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -t mangle -F[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -t mangle -X[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# 4.1.1 Set policies[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]$IPTABLES -P INPUT DROP[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -P OUTPUT DROP[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -P FORWARD DROP[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]# 4.1.2 Create userspecified chains
[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -N bad_tcp_packets[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -N allowed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -N tcp_packets[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -N udp_packets[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -N icmp_packets[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# 4.1.3 Create content in userspecified chains[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]# bad_tcp_packets chain[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -j REJECT --reject-with tcp-reset [/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "New not syn:"[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j DROP[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# allowed chain[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A allowed -p TCP --syn -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A allowed -p TCP -m state --state ESTABLISHED,RELATED -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A allowed -p TCP -j DROP[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# TCP rules[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]#FTP[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -p TCP -s 0/0 --dport 21 -j allowed[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]#SSH[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -p TCP -s 0/0 --dport 22 -j allowed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]#HTTP[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]#$IPTABLES -A tcp_packets -p TCP -s 0/0 --dport 80 -j allowed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]#WebMin[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -p TCP -s 192.168.0.0/16 --dport 10000 -j allowed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -p TCP -s 193.144.201.0/24 --dport 10000 -j allowed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]# Samba TCP ports: 139, 445 (from inner LAN)[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -m state --state NEW -m tcp -p TCP -s 192.168.0.0/16 --dport 139 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -m state --state NEW -m tcp -p TCP -s 192.168.0.0/16 --dport 445 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]# Samba TCP ports: 139, 445 (from Internet)[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -m state --state NEW -m tcp -p TCP -s 193.144.201.0/24 --dport 139 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A tcp_packets -m state --state NEW -m tcp -p TCP -s 193.144.201.0/24 --dport 445 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# UDP ports[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]# Samba UDP ports: 137, 138 (from inner LAN)[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A udp_packets -p UDP -m udp -s 192.168.0.0/16 --dport 137 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A udp_packets -p UDP -m udp -s 192.168.0.0/16 --dport 138 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]# Samba UDP ports: 137, 138 (from Internet)[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A udp_packets -p UDP -m udp -s 193.144.201.0/24 --dport 137 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A udp_packets -p UDP -m udp -s 193.144.201.0/24 --dport 138 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Accept echo request[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A icmp_packets -p ICMP -s 0/0 --icmp-type 8 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]# Accept TTL Exceeded[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A icmp_packets -p ICMP -s 0/0 --icmp-type 11 -j ACCEPT[/COLOR][/FONT]
[FONT=courier new]
[COLOR=#000000]# 4.1.4 INPUT chain[/COLOR]
[COLOR=#000000]# Bad TCP packets we don't want.$IPTABLES -A INPUT -p tcp -j bad_tcp_packets[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Rules for special networks not part of the Internet[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ALL -i $LAN_IFACE -s $LAN1_IP_RANGE -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ALL -i $LAN_IFACE -s $LAN2_IP_RANGE -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ALL -i $LO_IFACE -s $LO_IP -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ALL -i $LO_IFACE -s $LAN_IP -j ACCEPT[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ALL -i $LO_IFACE -s $INET_IP -j ACCEPT[/COLOR][/FONT]
[FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Special rule for DHCP requests from LAN, which are not caught properly[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]# otherwise.[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p UDP -i $LAN_IFACE --dport 67 --sport 68 -j ACCEPT[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Rules for incoming packets from the internet.[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ALL -d $INET_IP -m state --state ESTABLISHED,RELATED -j ACCEPT[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p TCP -i $INET_IFACE -j tcp_packets[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p UDP -i $INET_IFACE -j udp_packets[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -p ICMP -i $INET_IFACE -j icmp_packets[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Log weird packets that don't match the above.[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A INPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-level 7 --log-prefix "IPT INPUT packet died: "[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# 4.1.5 FORWARD chain[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]# Bad TCP packets we don't want[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A FORWARD -p tcp -j bad_tcp_packets[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Accept the packets we actually want to forward[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A FORWARD -i $LAN_IFACE -j ACCEPT[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT[/COLOR]
[/FONT][FONT=courier new]
[COLOR=#000000]# Log weird packets that don't match the above.[/COLOR]
[COLOR=#000000]$IPTABLES -A FORWARD -m limit --limit 3/minute --limit-burst 3 -j LOG --log-level 7 --log-prefix "IPT FORWARD packet died: "

# 4.1.6 OUTPUT chain[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]# Bad TCP packets we don't want.[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A OUTPUT -p tcp -j bad_tcp_packets[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]# Special OUTPUT rules to decide which IP's to allow.#$IPTABLES -A OUTPUT -p ALL -s $LO_IP -j ACCEPT[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A OUTPUT -p ALL -s $LAN_IP -j ACCEPT[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A OUTPUT -p ALL -s $INET_IP -j ACCEPT[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# Log weird packets that don't match the above.[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -A OUTPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-level 7 --log-prefix "IPT OUTPUT packet died: "[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# 4.2 nat table[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# 4.2.4 PREROUTING chain[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]
# DNS (from 192.168.0.0/16 or 128.100.100.0/24)[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -t nat -A PREROUTING -i $LAN_IFACE -p UDP -s 0/0 --destination-port 53 -j DNAT --to-destination $DNS_SERVER[/COLOR]
[/FONT][FONT=courier new]
[/FONT][FONT=courier new][COLOR=#000000]# 4.2.5 POSTROUTING chain[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]# Enable simple IP Forwarding and Network Address Translation[/COLOR]
[/FONT][FONT=courier new][COLOR=#000000]$IPTABLES -t nat -A POSTROUTING -o $INET_IFACE -j SNAT --to-source $INET_IP[/COLOR]
[/FONT]

```

---

