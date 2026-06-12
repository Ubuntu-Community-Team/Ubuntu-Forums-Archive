---
title: "NAT / Internet Conneciton Sharing / Router / IP Masquerading - Do it all here."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Rogers on 2008-02-18
So today I started looking to forward some ports to one of my internet boxes through my Linux router… problems ahoy.  I was using an outdated program called ipmasq which manages the MASQUERADING or forwarding automatically. Which is great out of the box but has no documentation and the source site has a manual that links to a penis enlargement add.

Great I thought.  Apt-get remove ipmasq was the obvious answer… and then my network went dead behind my router.   Searching google and the ubuntuforums.org I found little to help me and a lot of confusion.

From this I’ve learned:

    * IPMASQERADING is so easy no one talks about it, but there is little CLEAR and CONCISE documentation ANYWHERE.
    * Using weird 3rd party tools to do 3 basic commands in not effective system administration. Learn the system and you don’t need whacky tools.
    * iptables is truely sweet.

Here is a basic script that show exactly how to turn NAT/Routing/Masquerading on in a few lines along with how to forward ports.  It’s so basic it’s awesome.  Please post if this helps you.
[I]
##########################

#

#    NAT - FIREWALL SCRIPT v1.0

#

##########################

#  Author: [email]matt@runithard.com[/email]

##########################

#GLOBAL SETTINGS

IPTABLES=/sbin/iptables

NETWORK_RANGE='192.168.0.0/24'

EXTERNAL_INTERFACE="eth0"

#TURNS ON NAT/ICS

 /bin/echo "1" > /proc/sys/net/ipv4/ip_forward

$IPTABLES -A FORWARD -i eth1 -o $EXTERNAL_INTERFACE -s $NETWORK_RANGE -m state --state NEW -j ACCEPT

$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPTABLES -A POSTROUTING -t nat -j MASQUERADE

#FORWARD CODE TCP

$IPTABLES -A FORWARD -i $EXTERNAL_INTERFACE -d 192.168.0.100 -p tcp --dport 7777 -j ACCEPT

$IPTABLES -t nat -A PREROUTING -i $EXTERNAL_INTERFACE -p tcp --dport 7777 -j DNAT --to-destination 192.168.0.100:7777

#FORWARD CODE UDP

$IPTABLES -A FORWARD -i $EXTERNAL_INTERFACE -d 192.168.0.100 -p udp --dport 7777 -j ACCEPT

$IPTABLES -t nat -A PREROUTING -i $EXTERNAL_INTERFACE -p udp --dport 7777 -j DNAT --to-destination 192.168.0.100:7777[/I]


If you want to know

Source Blog: [http://runithard.com/?p=15]("http://runithard.com/?p=15"):)


Also, if you're going to run DHCPD (the daemon for DHCP).  Here is my file for example.  Hope this helps.
[I]
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $
#

# option definitions common to all supported networks...

authoritative;
default-lease-time 600;
max-lease-time 7200;
option domain-name-servers ns1,ns1;
#option domain-name "revolutionaryit.com";
option routers 192.168.0.1;
option broadcast-address 192.168.0.255;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.254;
  option subnet-mask 255.255.255.0;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host enterprise {
#  hardware ethernet MAC-HERE;
#  fixed-address  192.168.0.100;  
#}[/I]

---

