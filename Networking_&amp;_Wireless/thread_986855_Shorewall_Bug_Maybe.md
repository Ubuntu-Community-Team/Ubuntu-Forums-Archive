---
title: "Shorewall Bug? Maybe?"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Kylibar on 2008-11-19
Please forgive me for any typos, mis-spellings and whatnot... i have a bb/pellett in my thumb-gettin it out today :) woo! i can type agian

I have been issued a class A subnet from my service provider.
I will call this net 10.10.10.64/29. (this is not my real IP address - just a "real" example :)
10.10.10.64 is the network address
10.10.10.71 is the braodcast address
I have five useable static IP address; 10.10.10.(65 - 70)

THE MODEM
==============================================
The modem is in bridge mode. The PPPoE connection is executed by the firewall.
The modem's external address is assigned to me dynamically via the PPP connection from the firewall. Can't ever tell what that address is going to be.

I have assigned the INTERNAL address 10.10.10.64 (my broadcast address).
the netmask i gave it was 255.255.255.0

THE FIREWALL
==============================================
eth0;
This is the primary interface on my firewall.
It is assigned the address 10.10.10.65 (the first of my useable static IP address)
eth0 is bridged with ppp0? I think. to come up with the internet connection. You can see all of my statics from the external, but for simplicity I am just using 64 and 65 until I finally get it working right. oh yea, I used "pppoeconf" to configure my PPPoE connection with my modem and ISP. nothin special.

So my problems are:
I can logon with the ppp0 connection and surf the internet just fine with the FIREWALL only. The remaining computers connected to eth1 and eth2 CANNOT surf the internet. What is weird... is shorewall is WORKING? properly? I can get on any of the machines connected to either zone (eth1 or eth2) and logon to the 10.10.10.64 (the web-interface for the modem - which is connected to eth0), but I cant surf the net. So I know I can see through the firewall correctly. Its as if its a nameserver/name resolving issue? maybe I should install bind9? or does it have something to do with shorewall's setup? configuration setting? or my interface settings? im at a loss. I havent looked into the PPP config files. Maybe thats it? Or maybe if I bridge the three interfaces and then use the ppp. i dunno.

basically... everything on the interfaces eth1 and eth2 cannot see the internet. the firewall can see the internet. the internet is connected to the firewall via eth0 and ppp0.

any help would be nice.

also, does anyone know where I can find some good examples of the files used in PPP?? I understand what some lines of the config files mean. i dont know what alot of them mean though. maybe the reason the other 2 interfaces arent working lies somewhere in the ppp/pppoe config??

like i said, any help would be nice.



Here are ALL the config files. If you need anything else... just ask.

[HTML]
====================================================
Network Topology
====================================================

modem <---eth0--->  Shorewall$FireWall  <---eth1---> dmz zone

                         /\
                          |
                          |eth2
                          |
                         \/
                      loc zone





====================================================
Network Configuration Files
====================================================

/etc/networking/interfaces
####################################################
auto lo
iface lo inet loopback
#
auto eth0
iface eth0 inet static
address		10.10.10.65 ##not the real address but close enough
gateway		10.10.10.64 ##not the real address but close enough
netmask		255.255.255.0
	up ifup ppp0
	down ifdown ppp0
auto ppp0
iface ppp0 inet ppp
provider	dsl-provider
	#pre-up ifup eth0
	#post-down ifdown eth0
#
auto eth1
iface eth1 inet static
address		192.168.0.1
netmask		255.255.255.0
#
auto eth2
iface eth2 inet static
address		192.168.2.1
netmask		255.255.255.0
####################################################

/etc/resolv.conf
####################################################
#it contains my ISP nameservers
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
####################################################





====================================================
PPP Config Files
====================================================

/etc/ppp/chap secrets
####################################################
# Secrets for authentication using CHAP
# client	server	secret			IP addresses





"myemail@mydomain.com" * "mypassword"
####################################################

/etc/ppp/options
####################################################
#this file was alot larger, but i shrank it
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx
# ---<End of File>---
####################################################

/etc/ppp/pap-secrets
####################################################
#
# /etc/ppp/pap-secrets
#
# This is a pap-secrets file to be used with the AUTO_PPP function of
# mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option
# which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)
# after a user has passed this file. Don't be disturbed therefore by the fact
# that this file defines logins with any password for users. /etc/passwd
# (again, /etc/shadow, too) will catch passwd mismatches.
#
# This file should block ALL users that should not be able to do AUTO_PPP.
# AUTO_PPP bypasses the usual login program so it's necessary to list all
# system userids with regular passwords here.
#
# ATTENTION: The definitions here can allow users to login without a
# password if you don't use the login option of pppd! The mgetty Debian
# package already provides this option; make sure you don't change that.

# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*	hostname	""	*

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest	hostname	"*"	-
master	hostname	"*"	-
root	hostname	"*"	-
support	hostname	"*"	-
stats	hostname	"*"	-

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password





"myemail@mydomain.com" * "mypassword"
####################################################

/etc/ppp/peers/dsl-provider
####################################################
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "myemail@mydomain.com"

####################################################

/etc/ppp/peers/provider
####################################################
# Serial device to which the modem is connected.
/dev/modem

# Speed of the serial line.
115200

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth


####################################################





====================================================
Shorewall Configuration Files
====================================================

/etc/shorewall/interfaces
####################################################
#ZONE	INTERFACE	BROADCAST	OPTIONS
net	ppp0
net     eth0            detect          tcpflags,dhcp,routefilter,norfc1918,nosmurfs,logmartians
dmz     eth1            detect
loc     eth2            detect          tcpflags,detectnets,nosmurfs
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
####################################################

/etc/shorewall/masq
####################################################
#INTERFACE		SUBNET		ADDRESS		PROTO	PORT(S)	IPSEC
ppp0			eth0
eth0			eth1
eth0			eth2
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
####################################################

/etc/shorewall/policy
####################################################
#SOURCE		DEST		POLICY		LOG LEVEL	LIMIT:BURST
loc		net		ACCEPT
# If you want open access to the Internet from your Firewall
# remove the comment from the following line.
$FW		net		ACCEPT
# Also If You Wish To Open Up DMZ Access To The Internet
# remove the comment from the following line.
dmz		net		ACCEPT
net		all		DROP		info
# THE FOLLOWING POLICY MUST BE LAST
all		all		REJECT		info
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
####################################################

/etc/shorewall/routestopped
####################################################
#INTERFACE	HOST(S)
eth1		-
eth2		-
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
####################################################

/etc/shorewall/rules
####################################################
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/
#							PORT	PORT(S)		DEST		LIMIT		GROUP
#
#	Accept DNS connections from the firewall to the Internet
#
DNS/ACCEPT	$FW		net
#
#
#	Accept SSH connections from the local network to the firewall and DMZ
#
SSH/ACCEPT      loc             $FW
SSH/ACCEPT      loc             dmz
#
#	DMZ DNS access to the Internet
#
DNS/ACCEPT	dmz		net


# Reject Ping from the "bad" net zone.

Ping/REJECT     net             $FW

#
#       Make ping work bi-directionally between the dmz, net, Firewall and local zone
#       (assumes that the loc-> net policy is ACCEPT).
#

Ping/ACCEPT     loc             $FW
Ping/ACCEPT     dmz             $FW
Ping/ACCEPT     loc             dmz
Ping/ACCEPT     dmz             loc
Ping/ACCEPT     dmz             net

ACCEPT		$FW		net		icmp
ACCEPT		$FW		loc		icmp
ACCEPT		$FW		dmz		icmp

# Uncomment this if using Proxy ARP and static NAT and you want to allow ping from
# the net zone to the dmz and loc

#Ping/ACCEPT    net             dmz
#Ping/ACCEPT    net             loc

#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
####################################################

/etc/shorewall/shorewall.conf
####################################################
#the only changes I made were;
CLAMPMSS=Yes
IP_Forwarding=On
####################################################

/etc/shorewall/zones
####################################################
#ZONE	TYPE	OPTIONS			IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net	ipv4
loc	ipv4
dmz	ipv4
#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE
####################################################
[/HTML]

---

### Post by SpaceTeddy on 2008-11-19
first, pppoe.
When you establish a connection over pppoe you use a "normal" interface, but it gets overlayed with the ppp interface. This means, that although the real connection is on eth0, all traffic will ONLY arrive on ppp0 and DOES NOT go through eth0. In fact, you could even put a switch in between the modem and the server, configure eth0 with an internal address and use both (the ppp and the eth1) in different networks. This is normal behavior for pppoe (Hence ppp over Ethernet). Just forget about eth0 and only use ppp0.

Now, your other problem - First off - i have never used shorewall. So i don't know what it actually does - but i do know iptables, and i know that shorewall does create iptables rules. That said - there are several things that could be wrong here. 
1.) Forwarding is not done right, i.e. ip_forwarding is turned off in your kernel
2.) your firewall does not allow any traffic to pass through it (i.e. misconfigured FORWARD chain)
3.) you do not have masquerading enabled.
4.) your DNS is not setup properly.
5.) your DHCP does not work as expected. 

To debug this a little further, i need you to run a few commands and give me the output.

```
sudo iptables -L -vnx
sudo iptables -L --table nat -vnx
route -n
sudo sysctl net.ipv4.ip_forward
cat /proc/sys/net/ipv4/ip_forward
sudo netstat -lnp
cat /etc/resolv.conf

```

The first two will output your firewall (filter and nat table)
The third will show your routing
The fourth and fifth will show the status of your ip_forwarding in kernel
The sixth will display any running service on the server
The last will display the nameservers of the server.

lets see if we can figure this out :)

AS a sidenode - where did you read that this is a class A network ? i always thought that class A network are /8 in between 0.0.0.0 and 127.0.0.0... but maybe i am wrong ?

---

### Post by Kylibar on 2008-11-19
Now remember, im trying to get everything on eth1 and eth2 to see the internet. the modem is connected to eth0. im sure you know all of this alot better than I.

[HTML]
iptables -L -vnx OUTPUT
############################################
Chain Drop (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 reject     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:113
      10     1126 dropBcast  all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 code 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11
      10     1126 dropInvalid  all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,445
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:137:139
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:137 dpts:1024:65535
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:1900
       3      148 dropNotSyn  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:53

Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
      24     2328 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
    1730  1173182 ppp0_in    all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0
       0        0 eth0_in    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0
       0        0 eth1_in    all  --  eth1   *       0.0.0.0/0            0.0.0.0/0
       0        0 eth2_in    all  --  eth2   *       0.0.0.0/0            0.0.0.0/0
       0        0 Reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:INPUT:REJECT:'
       0        0 reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       1       48 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU
      15      860 ppp0_fwd   all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0
       0        0 eth0_fwd   all  --  eth0   *       0.0.0.0/0            0.0.0.0/0
       0        0 eth1_fwd   all  --  eth1   *       0.0.0.0/0            0.0.0.0/0
       3      228 eth2_fwd   all  --  eth2   *       0.0.0.0/0            0.0.0.0/0
       0        0 Reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:FORWARD:REJECT:'
       0        0 reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP 1 packets, 52 bytes)
    pkts      bytes target     prot opt in     out     source               destination
      24     2328 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
    1945   214120 fw2net     all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0
      30     2120 fw2net     all  --  *      eth0    0.0.0.0/0            0.0.0.0/0
       0        0 fw2loc     all  --  *      eth2    0.0.0.0/0            192.168.2.0/24
       0        0 fw2loc     all  --  *      eth2    0.0.0.0/0            255.255.255.255
       0        0 fw2loc     all  --  *      eth2    0.0.0.0/0            224.0.0.0/4
       0        0 fw2dmz     all  --  *      eth1    0.0.0.0/0            0.0.0.0/0
       0        0 Reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:OUTPUT:REJECT:'
       0        0 reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain Reject (4 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 reject     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:113
       0        0 dropBcast  all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 code 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11
       0        0 dropInvalid  all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 reject     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,445
       0        0 reject     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:137:139
       0        0 reject     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:137 dpts:1024:65535
       0        0 reject     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:1900
       0        0 dropNotSyn  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:53

Chain all2all (6 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 Reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:all2all:REJECT:'
       0        0 reject     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain dmz2fw (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 all2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain dmz2loc (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 all2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain dmz2net (2 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain dropBcast (2 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = broadcast
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = multicast

Chain dropInvalid (2 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID

Chain dropNotSyn (2 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:!0x17/0x02

Chain dynamic (8 references)
    pkts      bytes target     prot opt in     out     source               destination

Chain eth0_fwd (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 smurfs     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 tcpflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0
       0        0 net2all    all  --  *      eth2    0.0.0.0/0            192.168.2.0/24
       0        0 net2all    all  --  *      eth1    0.0.0.0/0            0.0.0.0/0

Chain eth0_in (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 smurfs     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
       0        0 tcpflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 net2fw     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain eth1_fwd (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 dmz2net    all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0
       0        0 dmz2net    all  --  *      eth0    0.0.0.0/0            0.0.0.0/0
       0        0 dmz2loc    all  --  *      eth2    0.0.0.0/0            192.168.2.0/24

Chain eth1_in (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 dmz2fw     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain eth2_fwd (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       3      228 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       3      228 smurfs     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 tcpflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
       3      228 loc2net    all  --  *      ppp0    192.168.2.0/24       0.0.0.0/0
       0        0 loc2net    all  --  *      eth0    192.168.2.0/24       0.0.0.0/0
       0        0 loc2dmz    all  --  *      eth1    192.168.2.0/24       0.0.0.0/0

Chain eth2_in (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 smurfs     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
       0        0 tcpflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 loc2fw     all  --  *      *       192.168.2.0/24       0.0.0.0/0

Chain fw2dmz (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 all2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain fw2loc (3 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 all2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain fw2net (2 references)
    pkts      bytes target     prot opt in     out     source               destination
    1544   189017 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
     281    18279 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53
       3      212 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
     147     8732 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain loc2dmz (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 all2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain loc2fw (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 all2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain loc2net (2 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       3      228 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain logflags (5 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 4 level 6 prefix `Shorewall:logflags:DROP:'
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain net2all (5 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
      10     1126 Drop       all  --  *      *       0.0.0.0/0            0.0.0.0/0
      10     1126 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:net2all:DROP:'
      10     1126 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain net2fw (2 references)
    pkts      bytes target     prot opt in     out     source               destination
    1720  1172056 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 reject     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
      10     1126 net2all    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain ppp0_fwd (1 references)
    pkts      bytes target     prot opt in     out     source               destination
      15      860 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
      15      860 ACCEPT     all  --  *      eth0    0.0.0.0/0            0.0.0.0/0
       0        0 net2all    all  --  *      eth2    0.0.0.0/0            192.168.2.0/24
       0        0 net2all    all  --  *      eth1    0.0.0.0/0            0.0.0.0/0

Chain ppp0_in (1 references)
    pkts      bytes target     prot opt in     out     source               destination
      10     1126 dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
    1730  1173182 net2fw     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain reject (11 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = broadcast
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = multicast
       0        0 DROP       all  --  *      *       68.16.236.255        0.0.0.0/0
       0        0 DROP       all  --  *      *       192.168.0.255        0.0.0.0/0
       0        0 DROP       all  --  *      *       192.168.2.255        0.0.0.0/0
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0
       0        0 DROP       all  --  *      *       224.0.0.0/4          0.0.0.0/0
       0        0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset
       0        0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
       0        0 REJECT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-unreachable
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

Chain shorewall (0 references)
    pkts      bytes target     prot opt in     out     source               destination

Chain smurfs (4 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 LOG        all  --  *      *       68.16.236.255        0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
       0        0 DROP       all  --  *      *       68.16.236.255        0.0.0.0/0
       0        0 LOG        all  --  *      *       192.168.0.255        0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
       0        0 DROP       all  --  *      *       192.168.0.255        0.0.0.0/0
       0        0 LOG        all  --  *      *       192.168.2.255        0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
       0        0 DROP       all  --  *      *       192.168.2.255        0.0.0.0/0
       0        0 LOG        all  --  *      *       255.255.255.255      0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0
       0        0 LOG        all  --  *      *       224.0.0.0/4          0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
       0        0 DROP       all  --  *      *       224.0.0.0/4          0.0.0.0/0

Chain tcpflags (4 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 logflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29
       0        0 logflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00
       0        0 logflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06
       0        0 logflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03
       0        0 logflags   tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spt:0 flags:0x17/0x02
###############################################################

iptables -L --table nat -vnx OUTPUT


Chain PREROUTING (policy ACCEPT 58 packets, 3440 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 774 packets, 48693 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     722    45845 ppp0_masq  all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0
      52     2848 eth0_masq  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT 735 packets, 46717 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain eth0_masq (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 MASQUERADE  all  --  *      *       192.168.0.0/24       0.0.0.0/0
       0        0 MASQUERADE  all  --  *      *       192.168.2.0/24       0.0.0.0/0

Chain ppp0_masq (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 MASQUERADE  all  --  *      *       68.16.236.0/24       0.0.0.0/0
###############################################################
route -n OUTPUT

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
65.14.248.8     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
68.16.236.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
###########################################################

sysctl net.ipv4.ip_forward OUTPUT

net.ipv4.ip_forward = 1
############################################################
cat /proc/sys/net/ipv4/ip_forward OUTPUT

1
############################################################
netstat -lnp OUTPUT

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3020/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     8764     3703/gam_server     @/tmp/fam-root-
unix  2      [ ACC ]     STREAM     LISTENING     8526     3616/kdm            /var/run/xdmctl/dmctl/socket
unix  2      [ ACC ]     STREAM     LISTENING     8536     3616/kdm            /var/run/xdmctl/dmctl-:0/socket
unix  2      [ ACC ]     STREAM     LISTENING     8532     3618/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8648     3665/ssh-agent      /tmp/ssh-pXFnoy3629/agent.3629
unix  2      [ ACC ]     STREAM     LISTENING     8698     3694/kdeinit Runnin /tmp/ksocket-root/kdeinit__0
unix  2      [ ACC ]     STREAM     LISTENING     8700     3694/kdeinit Runnin /tmp/ksocket-root/kdeinit-:0
unix  2      [ ACC ]     STREAM     LISTENING     8707     3697/dcopserver [kd /tmp/.ICE-unix/dcop3697-1226977994
unix  2      [ ACC ]     STREAM     LISTENING     9258     3777/artsd          /tmp/ksocket-root/FW-0ec1-492232db
unix  2      [ ACC ]     STREAM     LISTENING     8732     3699/klauncher [kde /tmp/ksocket-root/klaunchersTF8tc.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     9292     3783/ksmserver [kde /tmp/.ICE-unix/3783
#################################################################
cat /etc/resolv.conf OUTPUT

nameserver 205.152.37.23
nameserver 205.152.150.23

[/HTML]

---

### Post by SpaceTeddy on 2008-11-19
oh my god... that is a lot of rules. I'll need some time to look them over (not that i really know what shorewall is doing there). But, i have a few more questions...

If eth0 is only used for the uplink and being overlayed by pppoe, then why does it have a subnet and an ip ? this device should be blank with no configuration (as far as i am concerned with dsl, at least). Not that this is a problem - it is just not "clean" :)

the good new is - you seem to have ip_forwarding and your nameservers look correct. 

Mhm... looking over it again - you don't get any hits on the MASQUERADING chain in your nat table. This means that your packets don't get rewritten properly... I've just look over your shorewall config again, and i think i know why this is the case. In any way, this is just a blind guess, as i only know how to work iptables directly, and not shorewall - but, your masqueraing rules seem to wrong... 

try these:
> /etc/shorewall/masq
####################################################
#INTERFACE		SUBNET		ADDRESS		PROTO	PORT(S)	IPSEC
ppp0			eth1
ppp0			eth2
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
####################################################


if i see the translation from shorewall to iptables correctly, this should result in the correct masquerading rules and thus you will have packet rewriting... 

Again - this is just a guess. I'll also see if i can find anything else in the iptables dumps that looks odd to me...

---

### Post by Kylibar on 2008-11-19
if your a little curious how shorewall works (its for the most part..simple... ive had a previous and similar setup for the past year..works great.) anyway..its just a "frontend" to iptables. so you definitly know this stuff better than I. [www.shorewall.net](www.shorewall.net)   look at the basic 3interface setup (they can explain it faster than I) and thanks for helping me. ive been posting on this site for a little bit. i dont get help often :)


but im gonna try this out and let you know what happens.


ok, I decided to try that masq thing you mentioned. IT WORKS. I dont know WHY i didnt think of that!!! I feel like an idiot!!

[HTML]
##############################################################################
#INTERFACE		SUBNET		ADDRESS		PROTO	PORT(S)	IPSEC
ppp0			eth0
ppp0			eth1#i just added these lines
ppp0			eth2# and this one
eth0			eth1
eth0			eth2
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
[/HTML]

So, like I said. THANKS!! IVE BEEN WORKIN AT THIS FOR DAYS!!! Umm, im kinda new at this stuff but I learn fast. I soak in knowledge... so, if you want to critique my firewall... that would be great.

So for me to have an ULTRA secure firewall... how would I go about doing this? from the sounds of what your saying... my firewall isint really secure at all? (right now im just happy it works!!)

---

### Post by SpaceTeddy on 2008-11-19
you only need the two lines - as far as i understand the shorewall configuration, it says something like:
masquerade anything that leaves on this interfaces (ppp0) and comes from this interface (eth0)

since you only want to masquerade stuff that comes from eth1 and eth2 and goes out in ppp0 you only need the two rules i wrote... the other get 0 hits anyway (there is no traffic from eth0 to anywhere - that's what i was talking about overlaying the ppp0 device)

to be honest - i have serious trouble reading the shorewall configuration, and the iptables rules are a plain mess to me. this thing jumps rules here and there, drops and rejects stuff previous to accepting and after... not my idea of doing a clean firewall design. But then - it's me. 

Also, i am not really interested in learning shorewall. I had a look at it a few years back... but i really like to know what is actually happening than hoping that what i wrote to shorewall is what i think should be happening. I would never see in shorewall if a rule was used or not - i need iptables for that. So why use shorewall in the first place, if i have to resort to iptables for debugging later anyway... No - plain iptables is for me :)

anyway, i am glad i could help :)

---

