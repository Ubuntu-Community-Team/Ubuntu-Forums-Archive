---
title: "Networking with Ubuntu 6.10 server last hurdle &quot;yeah right&quot;"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by Bill007 on 2006-11-22
Well here I am again This time with some better News 

yeeee haaaa I am stoked to be able to control (talk at least as I really dont feel in control:rolleyes: )the server thru  PuTTy (saving me a lot of typing positive)

Not really sure where to go from here  

Server 6.10 Lamp (primarily a production server to be)

It has 

two Network cards configured to

** sudo nano /etc/network/interfaces** 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface Lan

auto eth1
iface eth1 inet static
address 192.168.2.100
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255


I have ssh PuTTy working like a treat from XP to the server

I can ping every Machine on the lan from the server

that has ip 
ip 192.168.1.1 ping good zero packet loss
ip 192.168.1.2 ping good zero packet loss
ip 192.168.1.3 ping good zero packet loss
ip 192.168.1.4 ping good zero packet loss
ip 192.168.1.5 ping good zero packet loss
ip 192.168.1.6 ping good zero packet loss

I dont seem to be able to find the Network card eth1
its setting are configured below

auto eth1
iface eth1 inet static
address 192.168.2.100
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255  Can some one please tell me if these are typical I was told in an earler forum that the ip on eth1 should be  

if eth0 = 192.168.1.x

then 

eth1 must be 192.168.2.x  


and that I shouldnt have  gateway configured is this right (clutching at straws here I know)

Just a last minute thought do I need to take the lan cord from eth1 and feed it directly to another network group THRU A SWITCH Ill feel stupid if thats it and can I feed the internet to all the computors on that group the more I write this the more sense it makes last hurdle I think for this part:-k

---

