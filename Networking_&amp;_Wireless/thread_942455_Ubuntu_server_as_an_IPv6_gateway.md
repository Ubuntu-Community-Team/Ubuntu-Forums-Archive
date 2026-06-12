---
title: "Ubuntu server as an IPv6 gateway"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by mievuan on 2008-10-09
Hi!
I'm having a bit of a troublesome situation with Ubuntu
servers and IPv6.
The situation is this:

My ISP is providing us with a block of IPv6 addresses. 
All traffic coming to this IPv6 network block is routed to me via a GRE tunnel. 
The GRE tunnel between me and my ISP is set up with these commands:
ip tunnel add ipv6tunnel mode gre remote <isp tunnel endpoint IPv4> local <my local tunnel endpoint IPv4> ttl 255
ip link set ipv6tunnel up
ip addr add 2001:a:b::2/64 dev ipv6tunnel #ipv6 address from the address block ISP has provided us 
ip -6 route add 2001::/3 dev ipv6tunnel

So this machine has a public IPv4 address (the tunnel endpoint IPv4) and an IPv6 network address from the 
ISPs address space (2001:a:b::2). I can use both of these addresses to connecting to and from this machine and everything works fine.


However this machine is acting as a bridge. The line from my ISP comes to eth0 of this machine and it's bridged with interface eth1 
that's connected to a switch. 
In this switch I have other Ubuntu machines that I need to configure so that they too would have
IPv6-addresses from that address block my ISP has provided. Their IPv6-traffic would then 
go to this machine which is running the GRE tunnel and get routed through this tunnel.

I'm really not an experienced network or linux guru and I don't really know what
steps would I need to take on this gateway machine that already has working IPv6, and on those
other machines, in order to get this to work.

I've tried to set up some kind of routing on one of these machines like this:
in /etc/network/interfaces:

iface eth0 inet6 static
        address 2001:a:b::3 #another IPv6 address from nyt ISPs block
        netmask 64
        pre-up modprobe ipv6
        up route -A inet6 add default gw ::1.2.3.4 #here the gw address is the IPv4 address of my GRE machines public IPv4 address

Now if I try to ping my GRE machines IPv6 address I get only this:

ping6 2001:a:b::2
PING 2001:a:b::2(2001:a:b::2) 56 data bytes
From 2001:a:b::3 icmp_seq=1 Destination unreachable: Address unreachable
From 2001:a:b::3 icmp_seq=2 Destination unreachable: Address unreachable

If I take tcpdump -n -i br0 icmp6 on my GRE tunneling machine, I can see queries that the pinging machine is sending but my gateway machine obviously doesn't respond?
tcpdump -n -i br0 icmp6
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br0, link-type EN10MB (Ethernet), capture size 96 bytes
15:43:18.807910 IP6 2001:a:b::3 > ff02::1:ff00:7: ICMP6, neighbor solicitation, who has 2001:a:b::2, length 32
15:43:19.807875 IP6 2001:a:b::3 > ff02::1:ff00:7: ICMP6, neighbor solicitation, who has 2001:a:b::2, length 32

Could someone point me out to the right direction here? What am I doing wrong (I'm afraid there might be plenty of things...)?

---

### Post by jhenager on 2008-10-09
I know nothing about GRE tunnelling, and am new to ipv6 but just covered ipv6 in ICND2 today. Searching on "GRE tunnel +ipv6", this comes up first.
[http://lartc.org/howto/lartc.tunnel.gre.html](http://lartc.org/howto/lartc.tunnel.gre.html)
which says up top:
In Linux, you'll need the ip_gre.o module.

I hope this gives you some direction and/or help.

---

### Post by mievuan on 2008-10-11
> **jhenager said:**
> I know nothing about GRE tunnelling, and am new to ipv6 but just covered ipv6 in ICND2 today. Searching on "GRE tunnel +ipv6", this comes up first.
[http://lartc.org/howto/lartc.tunnel.gre.html](http://lartc.org/howto/lartc.tunnel.gre.html)
which says up top:
In Linux, you'll need the ip_gre.o module.

I hope this gives you some direction and/or help.

Thanks, I already studied that site when I was going through with GRE tunneling with my ISP. 

I believe that's not the problem anymore as the IPv6 traffic reaches my tunneling machine. Now it's just the question of how to get this tunneling server distribute IPv6 addresses to other machines in my switch and route traffic to them. I'm trying to install the dhcpv6-project server and clients now to see if they can offer a solution. Let's see how it goes.

---

