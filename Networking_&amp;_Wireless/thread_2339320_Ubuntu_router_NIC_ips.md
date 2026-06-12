---
title: "Ubuntu router NIC ips"
date: 2016-10-07
forum: Networking &amp; Wireless
---

### Post by pandey3 on 2016-10-07
Hi i am extreme newbie and started learning linux by DIY ubuntu router project

1. My config will be ADSL Modem---Router/Gateway-Clients, what ip address should i assign to my modem,wan nic,internal lan nic .
2. How do i dial modem from my router

---

### Post by TheFu on 2016-10-07
Welcome to the forums.

If you are running a router, that makes you the "network administrator" so you need to know enough about networking to setup a subnet, gateway, DNS, and assign client IPs appropriately.  "Security Now" episodes 25 thru about 30 explain how the internet works. That would be a good primer.

The WAN IP should be provided by your ISP.  That can happen multiple ways depending on the connection type. For most home connections, that would be via DHCP, so you don't actually assign the address, but the connection client does.  IME, DSL connections tend to use PPP connections for authentication and requesting the WAN-side IP/network information.  Your ISP should have a how-to guide for this somewhere.  I haven't used ppp since '98, so don't know which program should be used.

For your internal LAN, you'd most likely (there are exceptions), want to use a non-routable private address space.  These are in the 192.168.x.x/24 or 172.16.x.x/16 or 10.x.x.x/8 ranges.  Pick one and use a /24 subnet to keep it simple. That will provide 254 internal IPs for "stuff" - more than most people need by far. Heck, I'm using about 60 internal IPs here and I'm a crazy-guy with devices, networking, subnetting, etc.  Even if you have 1 client, using the /24 is normal.

BTW, the router how-to should have provided reasonable examples for this stuff.

After reviewing the information listed above, feel free to ask for more help.

---

### Post by pandey3 on 2016-11-02
Thanks for the tip as i am extreme newbie and learning concepts on the way . i am going through tutorials in wiki and you tube but there is no definative answers 

1. As i connect 2 nics ifconfig shows wan card managed by ppp(when i dial my modem from router

a. should i give fixed ip to wan card or let it be managed by ppp.
b  in some tutorials it states that wan ip should be the default route, but when there is no ip for wan card in case of ppp dial my default route does not show

2. When using webmin , my internal nic shows enp3s0, and enp3s0.avahi in which interface should i provide dhcp

---

