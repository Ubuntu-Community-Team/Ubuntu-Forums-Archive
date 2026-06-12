---
title: "ubuntu as gateway router with iptables problem"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by thomax on 2008-10-14
Hi,

Ok, so I've set up an old xubuntu box as my router

modem <<-->> xubuntu router <<-->> hosts

My modem is a ADSL2+ modem in bridged mode to which I log in using PPPoE.

This brings up the interface ppp0

Ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:04:ac:39:ee:d1
          inet addr:172.19.3.2  Bcast:172.19.255.255  Mask:255.255.0.0
          inet6 addr: fe80::204:acff:fe39:eed1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1428859 errors:1 dropped:0 overruns:0 frame:1
          TX packets:701681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1140204899 (1.0 GB)  TX bytes:127893128 (121.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:05:5d:de:d2:5b
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fede:d25b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:716148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:933749 errors:2 dropped:0 overruns:2 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:128507615 (122.5 MB)  TX bytes:1104541415 (1.0 GB)
          Interrupt:11 Base address:0x4f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22508 (21.9 KB)  TX bytes:22508 (21.9 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:62.235.154.145  P-t-P:62.235.154.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1413757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:689551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1087682995 (1.0 GB)  TX bytes:110912040 (105.7 MB)
```

eth0 is my external interface with ip 172.19.3.2 to connect to the modem.

eth1 is my internal interface with ip 192.168.1.1 connected to a switch

ppp0 is my PPPoE interface with dynamic IP

Kernel IP routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.235.154.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
172.19.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

The internet works for the hosts on the network but I can't get my ports forwarded for httpd, ftp, torrent, etc. to the lan hosts.

I've got 2 working firewall scrips that seem to work fine (except for the port forwarding).

Most of all I would like to get port forwarding working on this first script, because (as far as I can tell) it looks the most secure.
```
#!/bin/sh

###################################
#                                 #
# IP Firewall script for          #
# PCC-Services                    #
# Author: Mike Petersen           #
#                                 #
###################################

# Configuration Options

EXTERNAL_INTERFACE="ppp0"
LOOPBACK_INTERFACE="lo"
LAN_INTERFACE_1="eth1"


# Get the IP Addresses for the network cards
IPADDR=`/sbin/ifconfig $EXTERNAL_INTERFACE | grep -i "addr:" | cut -f2 -d: | cut -f1 -d " "`
LAN_IPADDR=`/sbin/ifconfig $LAN_INTERFACE_1 | grep -i "addr:" | cut -f2 -d: | cut -f1 -d " "`
LOCALHOST_IP="127.0.0.1/32"
LAN_BCAST_ADDRESS="192.168.1.255"


##########

echo "Starting Firewalling... "
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -F

########## Enable Masquerading

iptables -t nat -A POSTROUTING -o $EXTERNAL_INTERFACE -j MASQUERADE
iptables -A FORWARD -i $LAN_INTERFACE_1 -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

########## Log errors when masquerading
iptables -A FORWARD -m limit --limit 3/minute --limit-burst 3 -j LOG --log-level DEBUG --log-prefix "IPT FORWARD packet died: "

########## Set default policies
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -i $LOOPBACK_INTERFACE -j ACCEPT
iptables -A OUTPUT -o $LOOPBACK_INTERFACE -j ACCEPT

########## Create Seperate Chains for ICMP, TCP and UDP to traverse

iptables -N icmp_packets
iptables -N tcp_packets
iptables -N udpincoming_packets

########## The Allowed Chain for TCP connections

iptables -N allowed
iptables -A allowed -p TCP --syn -j ACCEPT
iptables -A allowed -p TCP -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A allowed -p TCP -j DROP

########## ICMP rules (Internet Control Message Protocol)

iptables -A icmp_packets -p ICMP -s 0/0 --icmp-type 0 -j ACCEPT
iptables -A icmp_packets -p ICMP -s 0/0 --icmp-type 3 -j ACCEPT
iptables -A icmp_packets -p ICMP -s 0/0 --icmp-type 5 -j ACCEPT
iptables -A icmp_packets -p ICMP -s 0/0 --icmp-type 11 -j ACCEPT

########## TCP rules (Transmission Control Protocol)

### FTP port
iptables -A tcp_packets -p TCP -s 0/0 --dport 21 -j allowed

### SSH port
iptables -A tcp_packets -p TCP -s 0/0 --dport 22 -j allowed

### SMTP Mail Server port
iptables -A tcp_packets -p TCP -s 0/0 --dport 25 -j allowed

### HTTP port
iptables -A tcp_packets -p TCP -s 0/0 --dport 80 -j allowed

### POP3 port
iptables -A tcp_packets -p TCP -s 0/0 --dport 110 -j allowed

### IRC port
iptables -A tcp_packets -p TCP -s 0/0 --dport 113 -j allowed

### IMAP port
iptables -A tcp_packets -p TCP -s 0/0 --dport 143 -j allowed

### No-ip DNS services port
iptables -A tcp_packets -p TCP -s 0/0 --dport 8245 -j allowed

### Example of Port Forwarding using Bittorrent Ports
#iptables -t nat -A PREROUTING -d $IPADDR -p tcp -m tcp --dport 49250 -j DNAT --to-destination 192.168.1.102

## Something I tried myself to get some ports forwarded, but to no avail :/
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.100:80
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 49250 -j DNAT --to-destination 192.168.1.102:49250

########## UDP ports (User Datagram Protocol)

iptables -A udpincoming_packets -p UDP -s 0/0 --source-port 53 -j ACCEPT
iptables -A udpincoming_packets -p UDP -s 0/0 --source-port 123 -j ACCEPT
iptables -A udpincoming_packets -p UDP -s 0/0 --source-port 2074 -j ACCEPT
iptables -A udpincoming_packets -p UDP -s 0/0 --source-port 4000 -j ACCEPT
iptables -A udpincoming_packets -p UDP -s 0/0 --source-port 143 -j ACCEPT

########## Prerouting chain - Check for obviously spoofed IP's

iptables -t nat -A PREROUTING -i $EXTERNAL_INTERFACE -s 192.168.0.0/16 -j DROP
iptables -t nat -A PREROUTING -i $EXTERNAL_INTERFACE -s 10.0.0.0/8 -j DROP
iptables -t nat -A PREROUTING -i $EXTERNAL_INTERFACE -s 172.16.0.0/12 -j DROP

########## INPUT chain # Establish the basic Input chain
##########      and filter the packets onto the correct chains.

iptables -A INPUT -p ICMP -i $EXTERNAL_INTERFACE -j icmp_packets
iptables -A INPUT -p TCP -i $EXTERNAL_INTERFACE -j tcp_packets
iptables -A INPUT -p UDP -i $EXTERNAL_INTERFACE -j udpincoming_packets

iptables -A INPUT -p ALL -i $LAN_INTERFACE_1 -d $LAN_BCAST_ADDRESS -j ACCEPT
iptables -A INPUT -p ALL -d $LOCALHOST_IP -j ACCEPT
iptables -A INPUT -p ALL -d $LAN_IPADDR -j ACCEPT
iptables -A INPUT -p ALL -d $IPADDR -m state --state ESTABLISHED,RELATED -j ACCEPT

########## ENABLE TO LOG ERRORS
iptables -A INPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-level DEBUG --log-prefix "IPT INPUT packet died: "

########## OUTPUT chain # Establish the basic Output chain
##########      and filter them onto the correct chain

iptables -A OUTPUT -p ALL -s $LOCALHOST_IP -j ACCEPT
iptables -A OUTPUT -p ALL -s $LAN_IPADDR -j ACCEPT
iptables -A OUTPUT -p ALL -s $IPADDR -j ACCEPT

########## ENABLE TO LOG ERRORS
iptables -A OUTPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-level DEBUG --log-prefix "IPT OUTPUT packet died: "

```

But if thats not possible I will work with this one (or something else you guys can come up with).
```
#!/bin/sh

#first flush everything

#
# reset the default policies in the filter table.
#
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

#
# reset the default policies in the nat table.
#
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
iptables -t nat -P OUTPUT ACCEPT

#
# reset the default policies in the mangle table.
#
iptables -t mangle -P PREROUTING ACCEPT
iptables -t mangle -P POSTROUTING ACCEPT
iptables -t mangle -P INPUT ACCEPT
iptables -t mangle -P OUTPUT ACCEPT
iptables -t mangle -P FORWARD ACCEPT

#
# flush all the rules in the filter and nat tables.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
#
# erase all chains that's not default in filter and nat table.
#
iptables -X
iptables -t nat -X
iptables -t mangle -X

# Custom configuration begins

# Allow unlimited traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Setting default filter policy
iptables -A INPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -P INPUT DROP

# Setup port forwarding
iptables -A FORWARD -i ppp0 -o eth1 -s 192.168.1.0/24 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Setup DNAT
# Port forward from internet (tcp/udp one rule each) port 6112 to computer 192.168.0.100 port 6112 on internal network
iptables -A PREROUTING -t nat -p tcp --dport 80 -i ppp0 -j DNAT --to 192.168.1.100:80
iptables -A PREROUTING -t nat -p udp --dport 49250 -i ppp0 -j DNAT --to 192.168.1.100:49250

#setup MASQUERADING for nat
iptables -A POSTROUTING -t nat -j MASQUERADE
```

If you need any more information, just ask ;-)

Thanx for your time

---

### Post by thomax on 2008-10-15
Bump :/

---

### Post by thomax on 2008-10-15
again bump :/

---

