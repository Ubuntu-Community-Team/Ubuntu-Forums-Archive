---
title: "ipsec tunnel stops all other web traffic"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by -nano- on 2007-08-08
Hi,

I have little problem after i start ipsec tunnel, I hope someone can help me.

I have been building up two linux routers using ubuntu server release.  My goal is to make Ipsec VPN tunnel between them and route any other than local network traffic directly to internet.

I used Firestarter to configure my firewall to share internet connection to other computers in network that works fine in both routers. (eth0=local 192.168.1/2.0 and eth1=public ip)

I also have managed to open ipsec tunnel between routers, but when i open/start tunnel it connects OK, but everything but local host traffic stops(means that i still can use Webmin). I can't even ping local computers from router not even other side of tunnel. Also I can't ping from network A host to network B host. I cant even browse web from router and problem is same at both ends.

I used openswan to ipsec, both computers have 2 network cards and other one is directly in internet with public ip other one is in LAN other router has subnet 192.168.1.0/24 and other one 192.168.2.0/24

I opened ports 50,500 and 4500 from both ends using Firestarter.

This is my ipsec conf file in router A:
conn test
	auth=esp
	authby=secret
	auto=add
	compress=no
	esp=3des-md5
	left=x.x.x.x  # (this line has public address of router A)
	leftnexthop=%defaultroute
	leftsubnet=192.168.1.0/24
	right=y.y.y.y  #(this line has puplic address of router B)
	rightnexthop=%defaultroute
	rightsubnet=192.168.2.0/24
	type=tunnel

This is my ipsec conf file in router B:

conn test
	auth=esp
	authby=secret
	auto=add
	compress=no
	esp=3des-md5
	left=y.y.y.y #(this line has puplic address of router B)
	leftnexthop=%defaultroute
	leftsubnet=192.168.2.0/24
	right=x.x.x.x  # (this line has public address of router A)
	rightnexthop=%defaultroute
	rightsubnet=192.168.1.0/24
	type=tunnel

So what i should do that i get everything workin correctly? please be free to ask more information. 
 
Thanks

- Henri-

---

