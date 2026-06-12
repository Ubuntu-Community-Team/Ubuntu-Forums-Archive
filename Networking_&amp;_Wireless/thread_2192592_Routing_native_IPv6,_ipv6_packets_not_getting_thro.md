---
title: "Routing native IPv6, ipv6 packets not getting through from clients"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by michaelnjensen on 2013-12-08
Hi,


I'm struggling like crazy getting my ubuntu firewall to work properly with ipv6, when i read old topics here / google for guides it all sounds really easy (tm), but i just can't get ipv6 routing to work at all, my main problem is 99% of all the ipv6 routing guides i can find assumes i want to get ipv6 through a tunnel, which isn't the case in my setup, but first let me explain what the overall setup is like:


1 VM (ubuntu acting as router)
 - 1 Public interface (native ipv4/ipv6).
 - 1 Internal "host" interface


1 VM (Windows 2012R2 guest, same result with a ubuntu guest)
 - 1 Internal interface

Both running on top of ESXi.


The configuration on the router is the following (ips changed):


ipv4/ipv6 forwarding enabled with:
sysctl -w net.ipv6.conf.all.forwarding=1
sysctl -w net.ipv4.ip_forwarding=1


/etc/network/interfaces:


auto eth0
iface eth0 inet static
	address 123.123.123.123
	netmask 255.255.255.248
	gateway 123.123.123.121
        
        up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
        up iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
        up iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
        up iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 3389 -j DNAT --to-destination 172.17.16.2
        down iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
        down iptables -D FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
        down iptables -D FORWARD -i eth1 -o eth0 -j ACCEPT


iface eth0 inet6 static
	address 2a01:1:1:1::1234
	netmask 64
	gateway fe80::1 # required by hosting company


auto eth1
iface eth1 inet static
	address 172.17.16.1
	netmask 255.255.255.0
	
iface eth1 inet6 static
	address 2a01:1:1:1::1235
	netmask 64
	# tried with gateway fe80::1, / ipv6 from eth0, neither worked


radvd.conf with:
interface eth1 {
        AdvSendAdvert on;
        prefix 2a01:1:1:1::/64 {
                AdvOnLink on;
                AdvAutonomous on;
        };
};


eth0 is the public interface, eth1 is the internal interface, the guest is configured by ipv6 autoconfiguration, the 


windows guests gets a correct ip from radvd, it can ping the ipv6 ip on eth1, it can't reach the one on eth0, or any other 


ipv6 address, ipv4 routing is working fine from the guest.


The strange thing is, i can ping ipv6 addresses from both interfaces on the actual router with:
ping6 -n 2a00:1450:4001:802::100e
ping6 -n 2a00:1450:4001:802::100e -I eth1


The end goal is to have all traffic from the internet to go through the router to filter on incoming ipv4/ipv6 traffic, and allowing the guests on the internal network to be able to get out to the internet with both ipv4/ipv6.


Am i missing something completely obvious?

---

### Post by michaelnjensen on 2013-12-08
> **michaelnjensen said:**
> 
The strange thing is, i can ping ipv6 addresses from both interfaces on the actual router with:
ping6 -n 2a00:1450:4001:802::100e
ping6 -n 2a00:1450:4001:802::100e -I eth1

Hmn digging further that doesn't seem to be the case, while the above works, if i do a traceroute:
traceroute6 google.com -s [COLOR=#000000]2a01:1:1:1::1234   

It works, but if i use the src addr from eth1:
[/COLOR]traceroute6 google.com -s [COLOR=#000000]2a01:1:1:1::1235
It just times out.  
[/COLOR]

---

### Post by 7182818 on 2013-12-10
My guess is that the problems arise from your two interfaces having IP addresses in the same subnet.  When the return traffic comes in on eth0 destined for 2a01:1:1:1::1235 I bet it is ignoring it because it is on the same subnet as it's configured IP and it isn't destined for it.  Try changing the subnet of eth1 to something else and see if that fixes things.

---

