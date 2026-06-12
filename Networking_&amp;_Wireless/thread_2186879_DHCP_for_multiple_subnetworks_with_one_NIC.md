---
title: "DHCP for multiple subnetworks with one NIC"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by vbogatov on 2013-11-09
Hi everybody, 
I am trying to run DHCP server on Ubuntu 12.04. I need to configure several pools (different subnetworks) using one interface card. 
So I have configured below:

1) [FONT=Consolas][COLOR=#000000]sudo nano /etc/network/interfaces[/COLOR][/FONT]

auto eth0
iface eth0 inet static  
address 192.168.2.2
netmask  255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameserver 192.168.2.1
dns-search juniperlab.info

2) [COLOR=#000000][FONT=Consolas]sudo nano /etc/default/isc-dhcp-server
INTERFACES="eth0"

[/FONT][/COLOR]3) [COLOR=#000000][FONT=Consolas]sudo nano /etc/dhcp/dhcpd.conf

[/FONT][/COLOR]ddns-update-style interim;
option domain-name "juniperlab.info";
option domain-name-servers juniperlab.info;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;


shared-network server {
   subnet 192.168.2.0 netmask 255.255.255.0 {
         range 192.168.2.10 192.168.2.100;
         default-lease-time 600;
         max-lease-time 7200;
         option routers 192.168.2.1;
         option broadcast-address 192.168.2.255;
         option subnet-mask 255.255.255.0;
         option ntp-servers 192.168.2.2;
         option domain-name-servers 192.168.2.2;
         }
   subnet 192.168.1.0 netmask 255.255.255.0 {
         range 192.168.1.10 192.168.1.100;
         default-lease-time 600;
         max-lease-time 7200;
         option routers 192.168.1.2;
         option broadcast-address 192.168.1.255;
         option subnet-mask 255.255.255.0;
         option ntp-servers 192.168.1.2;
         option domain-name-servers 192.168.1.2;
         }
   subnet 192.168.5.0 netmask 255.255.255.0 {
         range 192.168.5.10 192.168.5.100;
         default-lease-time 600;
         max-lease-time 7200;
         option routers 192.168.5.2;
         option broadcast-address 192.168.5.255;
         option subnet-mask 255.255.255.0;
         option ntp-servers 192.168.5.2;
         option domain-name-servers 192.168.5.2;
         }
}

[B]After all configurations - DHCP service is functional but it gives me only 192.168.1.0 subnet IP addresses :(

Can't understand what I do wrong, if any ideas please help.[/B]

---

### Post by tenmoi on 2013-11-09
You'd better read chapter 15 from DHCP Handbook - second edition. This is normal. Once the 198.168.1.0 range is used up, any of the remaining 2 will be used.

Regards,

P.S
Here's a quote 

'In fact, subnets are an artifact of the way IP addressing works. In order for IP routing
to work, all machines on a given subnet must be on a single network segment.
However, it is not required that only one IP subnet be configured on a single
network segment.
Some sites take advantage of this as a way of allocating address space; when a
network segment is first deployed, a single IP subnet is allocated for it. [B][U]When most
of the IP addresses on that network segment have been consumed, the site administrator
allocates a second IP subnet to run on the same network segment[/U][/B].'

---

### Post by vbogatov on 2013-11-10
Well I am trying to resolve a little bit other issue - is to distribute IP addresses to LAN segments (subnets) not just release IP addresses to one segment.((

---

### Post by tenmoi on 2013-11-10
Well, as far as I know you are asking too much of the DHCP server. Either you set up another server to deliver a different pool or your current server will only give your clients addresses from any of your three until it is deplete. Only then does it start to use any one of the remaining two. 

_**One DHCP server will only deliver one pool at a time regardless of how many subnets you declared**._ Now read this bold part as wrong. My apologies.

Regards,

---

### Post by vbogatov on 2013-11-10
In Windows Server you can resolve as many pools as you wish at a time, also Turbo DHCP in Windows 7 does the same,  I have tested it many times, the problem is how to arrange it in Linux.

---

### Post by tenmoi on 2013-11-11
That's Windows World. You are using ISC DHCP. As I said before, just grab a copy of The DHCP Handbook - 2nd edition and read chapter 20 to solve this problem.

P.S
I don't work in IT. I read computer books just to keep myself busy, so that's all that I can help.

Regards,

---

### Post by vbogatov on 2013-11-19
_**I have solved this problem, please check out my video **_[http://youtu.be/9RM2pXTk03w](http://youtu.be/9RM2pXTk03w), **and good luck;)**

---

