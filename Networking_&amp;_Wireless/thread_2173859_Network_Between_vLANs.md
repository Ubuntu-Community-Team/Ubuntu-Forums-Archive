---
title: "Network Between vLANs"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by MikeMunn on 2013-09-11
Ubuntu 12.04.3 LTS

I am having an issue allowing traffic between vlans. 

I have vlan200 as my device vlan @ 10.10.200.0/24
I have vlan202 as my 1st wireless vlan @ 10.10.202.0/23
I have vlan206 as my 2nd wireless vlan @ 10.10.206.0/24

I have DHCP set up on all three vlans and want my devices to receive DHCP on vlan200 but allow vlan202 and 206 to operate also. Not sure how this works. Please help.

---

### Post by MikeMunn on 2013-09-12
Nothing huh?

---

### Post by s-bodet on 2013-09-14
Assuming your interfaces are eth0 (10.10.200.254/24), eth1 (10.10.203.254/23), eth2 (10.10.206.254/24) correctly configured in /etc/network/interfaces

1) Edit /etc/default/isc-dhcp-server to let your server know that it will serve IP addresses along these Ethernet interfaces

INTERFACES="eth0 eth1 eth2"

2) Edit /etc/dhcp/dhcp.conf to configure your DHCP pools :


[SIZE=2][FONT=courier new]subnet 10.10.200.0 netmask 255.255.255.0 {
 option routers 10.10.200.254;
 option subnet-mask 255.255.255.0;
 option broadcast-address 10.10.200.255;
 option domain-name-servers 10.10.200.254;
 option domain-name "VLAN200";
 default-lease-time 600;
 max-lease-time 7200;
 range 10.10.200.10 10.10.200.50;
}

subnet 10.10.202.0 netmask 255.255.254.0 {
 option routers 10.10.203.254;
 option subnet-mask 255.255.254.0;
 option broadcast-address 10.10.203.255;
 option domain-name-servers 10.10.203.254;
 option domain-name "VLAN202";
 default-lease-time 600;
 max-lease-time 7200;
 range 172.202.10.10 10.10.202.50;
}

subnet 10.10.206.0 netmask 255.255.255.0 {
 option routers 10.10.206.254;
 option subnet-mask 255.255.255.0;
 option broadcast-address 10.10.206.255;
 option domain-name-servers 10.10.206.254;
 option domain-name "VLAN206";
 default-lease-time 600;
 max-lease-time 7200;
 range 10.10.206.10 10.10.206.50;
}[/FONT][/SIZE]

Obviously, adapt your configuration :-)
You may have different DNS, or you may want to serve other ranges than 10-50...

3) Restart dhcp 

[FONT=courier new]sudo service isc-dhcp-server restart[/FONT]


You can run Wireshark or tcpdump/dhcpdump on your server to check all DHCP Requests/Replies.

Steve

---

### Post by MikeMunn on 2013-09-25
Being slightly more clear. I have this in /etc/network/interfaces:

[SIZE=1][I]# The loopback network interface
auto lo
iface lo inet loopback

auto eth0 eth0:5 eth0:6 eth0:7 eth0:8 eth0:9 eth0:11 eth1 eth2 eth3 eth5 vlan5 vlan10 vlan109 vlan172 vlan173 vlan199 vlan200 vlan201 vlan202 vlan204 vlan205 vlan206

# WAN Interface
iface eth0 inet static
        address XXX.XXX.XXX.XXX
        netmask 255.255.255.252
        gateway XXX.XXX.XXX.XXX

# Internal NAT
iface eth1 inet static
        address 10.10.1.10
        netmask 255.255.0.0

iface eth2 inet static
        address 10.10.200.1
        netmask 255.255.255.0
        vlan_raw_device eth2


# VLAN 200 for AP Management
iface vlan200 inet static
        address 10.10.200.1
        netmask 255.255.255.0
        vlan_raw_device eth2

# VLAN 202 Guest Wireless
iface vlan202 inet static
        address 10.10.202.1
        netmask 255.255.254.0
        vlan_raw_device eth2

# [/I][/SIZE][SIZE=1]*VLAN 206 *[/SIZE][SIZE=1][I]Corp Wireless Network
iface vlan206 inet static
        address 10.10.206.1
        netmask 255.255.255.0
        vlan_raw_device eth2[/I][/SIZE]

[SIZE=2]This [/SIZE]is the firewall configuration

[SIZE=1][I]#!/bin/sh

echo "\nLoading Firewall...\n"

######################################################################################################
## Setting up Script program variables
######################################################################################################

IPTABLES=/sbin/iptables
ROUTE=/sbin/route
#PPTPPROXY=/sbin/pptpproxy

# Router Interfaces
###########################################
## Physical Interfaces

WANIFACE="eth0"
LANIFACE="eth1"
VLANTRUNKIFACE="eth2"

## VLAN Interfaces
VLAN200="vlan200" # Network Devices VLAN
VLAN202="vlan202" # Grove Hotel Guest Wireless VLAN
VLAN206="vlan206" # Arena Wireless VLAN

## VLAN Array for internet access Check line 153-154
INET_VLANS="$VLAN200 $VLAN202 $VLAN206"

# Router Networks
###########################################

## WAN Network to Metro Ethernet
WAN_NETWORK="XXX.XXX.XXX.001/30"

## CORP WAN Network
CORP_NETWORK1="XXX.XXX.001.001/28"
CORP_NETWORK2="XXX.XXX.002.001/29"


## VLAN Network
VL_SERVERS="10.10.15.0/24"
VL_DEVICES="10.10.200.0/24"

# SERVER IP ADDRESSES
###########################################
## EXTERNAL IP ADDRESSES TO BE PORT FORWARDED
VORTEX_EXT="XXX.XXX.001.005"
FRANKLIN_EXT="XXX.XXX.001.006"
BLUESOCKET_EXT="XXX.XXX.001.007"
ARENAGUEST_EXT="XXX.XXX.001.008"
FTP_EXT="XXX.XXX.001.009"
SURVEY_EXT="XXX.XXX.001.010"
NAVICOM_SRC="XXX.XXX.001.011"
BTV_EXT="XXX.XXX.001.012"

## INTERNAL IP ADDRESS FOR FORWARDING
FRANKLIN_INT="10.10.15.17"
VORTEX_VPN_INT="10.10.16.2"
VORTEX_INT="10.10.15.2"
FTP_INT="10.10.15.2"
SURVEY_INT="10.10.15.16"
BTV_INT="10.10.40.200"
BLUESOCKET_INT="10.10.200.3"

# Flushing and setting up Default Firewall Policies
###########################################

$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT ACCEPT
#IPTABLES -P INPUT DROP
$IPTABLES -F INPUT
#$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -P OUTPUT ACCEPT
#$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT

######################################################################################################
## Enabling NAT through POSTROUTING CHAIN for interface WANIFACE
echo "Loading POSTROUTING CHAIN..."
######################################################################################################

# TORRENT BLOCK #
#$IPTABLES -A OUTPUT -p tcp --destination-port 6881:6999 -j DROP
# Block by MAC or IP of known offenders
$IPTABLES -A INPUT -m mac --mac-source 00:1c:26:64:12:61 -j DROP
$IPTABLES -A FORWARD -p tcp -m mac --mac-source 00:1c:26:64:12:61 -j DROP
$IPTABLES -A FORWARD -p tcp -m mac --mac-source 34:15:9e:76:53:bd -j DROP
$IPTABLES -A INPUT -m mac --mac-source 60:33:4b:1d:12:08 -j DROP
$IPTABLES -A INPUT -m mac --mac-source 00:16:cb:b8:10:d8 -j DROP
$IPTABLES -A INPUT -m mac --mac-source 70:1a:04:4e:55:b7 -j DROP
$IPTABLES -A FORWARD -p TCP -m mac --mac-source 00:26:08:e9:e5:78 -j DROP
# END TORRENT BLOCK #

# Allowing NAT traffic

echo "  * Corp Network Rules..."
## External facing IP Address for the Corp Network
$IPTABLES -t nat -I POSTROUTING -o $WANIFACE -s 10.10.0.0/16 -j SNAT --to XXX.XXX.XXX.001


echo "  * Setting Exchange Exemption..."
#EXCHANGE EXEMPTION RULE
$IPTABLES -t nat -A PREROUTING -d 63.230.119.6 -m tcp -p tcp --dport 80 -j DNAT --to-destination 10.10.15.17
$IPTABLES -t nat -A POSTROUTING -d 10.10.15.17 -s 10.10.0.0/16 -j SNAT --to-source 10.10.200.1

## NAT OVERLOAD FOR NETWORK
echo "  * Loading NAT OVERLOAD Rules..."
$IPTABLES -t nat -A POSTROUTING -o $WANIFACE -j MASQUERADE

#echo "  * Applying POSTROUTING Chain logging for troubleshooting"
# General Logging
#$IPTABLES -t nat -A POSTROUTING -j LOG --log-prefix "POSTROUTE Chain: "
## DEBUGGING MODE
#$IPTABLES -t nat -I POSTROUTING -j LOG --log-prefix "POSTROUTE Chain: "

######################################################################################################
## Enabling PORT FORWARDING FOR CORP NETWORK 1
echo "Loading PREROUTING CHAIN..."
######################################################################################################

# Port forwarding for BTV
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $BTV_EXT -j DNAT --to $BTV_INT

# Port forwarding rules for FRANKLIN
## FRANKLIN SMTP Rules
echo "  * Loading Franklin Rules..."
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FRANKLIN_EXT -p tcp --dport 25 -j DNAT --to $FRANKLIN_INT

## FRANKLIN HTTP/HTTPS Rules
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FRANKLIN_EXT -p tcp --dport 80 -j DNAT --to $FRANKLIN_INT
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FRANKLIN_EXT -p tcp --dport 443 -j DNAT --to $FRANKLIN_INT
## FRANKLIN FTP/SFTP Rules
#$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FRANKLIN_EXT -p tcp --dport 20:21 -j DNAT --to $FRANKLIN_INT
#$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FRANKLIN_EXT -p tcp --dport 22 -j DNAT --to $FRANKLIN_INT
#$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FRANKLIN_EXT -j DROP

echo "  * Loading FTP Rules..."
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FTP_EXT -p tcp --dport 20:21 -j DNAT --to $FTP_INT
###$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FTP_EXT -j DROP

echo "  * Loading VPN01 (PPTP) Rules..."
$IPTABLES -t nat -I PREROUTING -i $WANIFACE -d $VORTEX_EXT -p 47 -j ACCEPT
$IPTABLES -t nat -I PREROUTING -i $WANIFACE -d $VORTEX_EXT -p tcp --dport 1723 -j DNAT --to $VORTEX_VPN_INT
###$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $VORTEX_EXT -j DROP

######################################################################################################
## Settings for INPUT CHAIN of FIREWALL
echo "Loading INPUT CHAIN..."
######################################################################################################
# Allow SSH connections from administrator's network and Nathans PPTP IP
echo "  * Loading SSH access to Router..."
$IPTABLES -A INPUT -s 10.10.50.102 -p tcp --dport 56565 -j ACCEPT
$IPTABLES -A INPUT -s 10.10.50.102 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A INPUT -s 10.10.50.102 -p tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -s 10.10.50.101 -p tcp --dport 80 -j ACCEPT
#$IPTABLES -A INPUT -s 10.10.250.1 -p tcp --dport 56565 -j ACCEPT
#$IPTABLES -A INPUT -s 10.10.250.1 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 -j DROP
$IPTABLES -A INPUT -p tcp --dport 56565 -j DROP
$IPTABLES -A INPUT -p tcp --dport 80 -j DROP

# Logging everything for troubleshooting purposes
#echo " * Applying INPUT Chain logging for troubleshooting"
## General LOGGING
#$IPTABLES -A INPUT -j LOG --log-prefix "INPUT Chain: "
## DEBUGGING MODE
#$IPTABLES -I INPUT -j LOG --log-prefix "INPUT Chain: "

######################################################################################################
## Settings for OUPUT CHAIN of FIREWALL
echo "Loading OUTPUT CHAIN..."
######################################################################################################

# Logging everything for troubleshooting purposes
#echo " * Applying OUTPUT Chain logging for troubleshooting"
#General logging
#$IPTABLES -A OUTPUT -j LOG --log-prefix "OUTPUT Chain: "
## DEBUGGING MODE
#$IPTABLES -I OUTPUT -j LOG --log-prefix "OUTPUT Chain: "


######################################################################################################
## Setting for FORWARD CHAIN of FIREWALL
echo "Loading FORWARD CHAIN..."
######################################################################################################

$IPTABLES -A FORWARD -p gre -j ACCEPT

# Allow Network to communicate through NAT
$IPTABLES -A FORWARD -i $WANIFACE -o $LANIFACE -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $WANIFACE -j ACCEPT

## VLAN Access Control Lists
echo "  * Applying VLAN ACL's"
######################################

#Devices Network
echo "    * Applying VLAN200 Devices Network"
$IPTABLES -A FORWARD -i vlan200 -o $WANIFACE -j ACCEPT
$IPTABLES -A FORWARD -i $WANIFACE -o vlan200 -j ACCEPT

$IPTABLES -A FORWARD -i vlan200 -o $LANIFACE -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o vlan200 -j ACCEPT

$IPTABLES -A FORWARD -i vlan202 -o $WANIFACE -j ACCEPT
$IPTABLES -A FORWARD -i $WANIFACE -o vlan202 -j ACCEPT

$IPTABLES -A FORWARD -i vlan206 -o $WANIFACE -j ACCEPT
$IPTABLES -A FORWARD -i $WANIFACE -o vlan206 -j ACCEPT

## ACCESS LIST TO ACCESS THE SERVER VLAN
## Monitoring Network
$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.200.0/24 -d 10.10.50.0/24 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.50.0/24 -d 10.10.200.0/24 -j ACCEPT

$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.200.0/24 -d 10.10.202.0/23 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.202.0/23 -d 10.10.200.0/24 -j ACCEPT

$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.200.0/24 -d 10.10.15.21 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.15.21 -d 10.10.200.0/24 -j ACCEPT

$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.201.0/24 -d 10.10.0.0/16 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.0.0/16 -d 10.10.201.0/24 -j ACCEPT

# Added for Phone System Network Access
$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.200.0/24 -d 10.10.109.0/24 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.109.0/24 -d 10.10.200.0/24 -j ACCEPT
$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.109.0/24 -d 10.10.50.0/24 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.50.0/24 -d 10.10.109.0/24 -j ACCEPT
$IPTABLES -A FORWARD -i $VLANTRUNKIFACE -o $LANIFACE -s 10.10.109.0/24 -d 10.10.15.0/24 -j ACCEPT
$IPTABLES -A FORWARD -i $LANIFACE -o $VLANTRUNKIFACE -s 10.10.15.0/24 -d 10.10.109.0/24 -j ACCEPT

#$IPTABLES -A FORWARD -i $LANIFACE -o $DMZIFACE -j ACCEPT
#$IPTABLES -A FORWARD -i $DMZIFACE -o $LANIFACE -j ACCEPT

# Logging everything for troubleshooting purposes
#echo " * Applying FORWARD Chain logging for troubleshooting"
## General Logging
#$IPTABLES -A FORWARD -j LOG --log-prefix "FORWARD Chain: "
## DEBUGGING MODE
#$IPTABLES -I FORWARD -j LOG --log-prefix "FORWARD Chain: "

# Adding Experimental MTU Clamping Support - 18APR2011
#$IPTABLES -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

echo "\nFirewall Script Loaded!\n"
echo "\nHave a nice day.\n"[/I][/SIZE]

Any ideas why now?

---

