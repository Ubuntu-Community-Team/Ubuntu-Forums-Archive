---
title: "public IP routing - need help!"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by romzilla on 2008-04-21
Hi all Ununtu fans! I am quite new with Ubuntu and Linux, just installed it this week. Why did I do it? The company where I work needs a new router, DNS and Web server(PHP + MySQL). But let’s start from the beginning – the router. I surfed the internet and found some interesting info about routing in Linux. I configured a router with NAT myself just for training. But that won’t do for my company. I need to make a router for public IP that we got from our ISP (IP used below are public, but do to privacy polices the beginning is changed to 200.200.200.xxx). So no NAT is needed, just IP forwarding in doth ways (as I understand it). No firewall as well, for a start.

internet--eth0-[router]-eth1—LAN

What did I do
1)	configured /etc/network/interfaces
auto eth0
iface eth0 inet static
address 200.200.200.246
netmask 255.255.255.252
gateway 200. 200. 200.245
network 200. 200. 200.244
broadcast 200. 200. 200.247

auto eth1
iface eth1 inet static
address 200.200.200.249
netmask 255.255.255.248
network 200. 200. 200.248
broadcast 200. 200. 200.255

2)	enabled ip forwarding
echo “1” > /proc/sys/net/ipv4/ip_forward

What do I have
1) Kernel IP routing table
Destination | Gateway | Genmask | Flags | Metric | Ref | Use | Iface
200. 200. 200. 244 | * | 255.255.255.252 | U | 0 | 0 | 0 | eth0
200. 200. 200. 248 | * | 255.255.255.248 | U | 0 | 0 | 0 | eth1
Link-local | * | 255.255.0.0 | U | 1000 | 0 | 0 | eth0
default | 200.200.200.245 | 0.0.0.0 | UG | 100 | 0 | 0 | eth0

2)	iptables –L
Chain INPUT (policy ACCEPT)
Chain FORWARD (policy ACCEPT)
Chain OUTPUT (policy ACCEPT)

From the local machine with address 200.200.200.250 I can ping 200.200.200.249 and 200.200.200.249, but can not go behind the router. The router itself has access to internet.
What can I say. This thing is simple for you, but I am desperate and need help please!

---

### Post by sKAApGIF on 2008-04-21
It doesn't seem like you have added any rules at all?

I'm not 100% sure but as far as I can remember this should work:
#Allow everything from the lan out:
iptables -A FORWARD -i $LAN -o $WAN -j ACCEPT
#Allow everything from the wan in:
iptables -A FORWARD -i $WAN -o $LAN -j ACCEPT

Where $LAN is the local interface, in your case eth1 and $WAN the internet interface in your case eth0.

Hope it helps.

---

### Post by romzilla on 2008-04-22
sKAApGIF tnank you for your answer!
I apllyed those rules and did /etc/init.d/networking restart. Now my iptables &#8211;L gives this
Chain INPUT (policy ACCEPT)
Chain FORWARD (policy ACCEPT)
target | prot | opt | source | destination
ACCEPT | 0 | -- | anywhere | anywhere
ACCEPT | 0 | -- | anywhere | anywhere
Chain OUTPUT (policy ACCEPT)

But the result still is the same. Routing does not work. Maybe you any more ideas what is wrong and how to fix it? I have a sence that problem is quite simple, but you need to know some feature to fix it!

---

### Post by sKAApGIF on 2008-04-23
I have no real experience with routing... but from what I read your original setup should work (since you have no firewall rules that would DROP any packets it's not necessary to ALLOW anything specific).  In other words you can flush your iptables.

If you ping from a computer behind router to the internet, what type of response do you get?  "Host not found" or "no route to host"?

Are the computers behind the router configured with a gateway address?  Their gateway address would be the ip of your router.

---

