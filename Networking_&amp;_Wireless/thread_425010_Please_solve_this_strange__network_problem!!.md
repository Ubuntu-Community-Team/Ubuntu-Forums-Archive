---
title: "Please solve this strange  network problem!!"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by amitava82 on 2007-04-27
I have this strange problem. first I'll give the facts then the problem.

my college wifi network  assign ip address using DHCP.
DHCP assigned ips are in rage of 192.168.0.0 to 192.168.1.0
proxy server is 192.168.1.2
for some weird reason DHCP assigned IP addresses are blocked for net. only ips in rage of 192.168.15.0 works for internet. so i set ip address manually.

now here is the problem. for obvious reason DHCP assigned ip address won't work, so i assign ip address manually for wireless card eth1. Say if i assign ip address to 192.168.15.244 and ping 192.168.1.2 i'm getting error msg "Network Unreachable". but other computers in ip ranges 192.168.15.0 are responding to ping. now if I assign ip address to 192.168.1.244 then it pings successfully to the proxy server. but internet does not work in 192.168.1.0 ip rages as they are blocked. I have the same configuration in WIndows XP i.e., 192.168.15.244 and i can ping  successfully the proxy server and i can browse internet. even my friend is also having the same problem with ubuntu 7.04. can someone solve this weird problem?  :confused:

---

### Post by joft on 2007-04-27
Which subet mask do you use? Or which one do you you use in Windows? Do you have any additional routes in Windows ("route print")?

Additionally, I suggest asking your network administrator about your choice of IP, because if everybody is using some random IP, there might be conflicts. You could ask about IP, subnet mask, default gateway and any other routes, which are usually sent by the DHCP server.

---

### Post by amitava82 on 2007-04-27
subnet mask is 255.255.255.0 and getway is 192.168.1.2. DHCP is assigning 255.255.0.0 subnet
there is no conflict in ip, i'm sure. why can't ubuntu ping different ip range?

EDIT: i tried ubuntu 6.06 live CD but same problem..

---

### Post by amitava82 on 2007-04-27
bump..

---

### Post by agurk on 2007-04-27
Try setting your subnet mask to 255.255.0.0

---

### Post by amitava82 on 2007-04-27
its not working.. only if i put these settings manually (in windows) then internet works:
ip: 192.168.15.*
subnet: 255.255.255.0
getway: 192.168.1.2
in windows it pings successfully but not in ubuntu with the same settings.. if i make it by DHCP then both the OSs pings but net does not work..

---

### Post by jpatton on 2007-04-27
You're able to ping folks in whatever subnet you are in, but are unable to ping out to the internet, is this correct? If that is so, sounds like you don't have the correct router identified, it will NOT be the proxy in the .1. range. You need to find a router that will allow connectivity out from the .15. subnet you have placed yourself.

You should also be careful, I work for a large university in Kansas and we actively monitor rogue computers on the network. From your original post it appears the university has blocked internet access for a reason, and by circumventing that, you could find yourself in trouble.

---

### Post by agurk on 2007-04-27
If the same settings work in Windows, they should work in Ubuntu. Something else must be wrong and I'm suspecting that it's your route table. Please open a terminal window and execute the following command:
```
route
```

---

### Post by amitava82 on 2007-04-28
here is the route output
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    *               255.255.255.0   U     0      0        0 eth1


here is the traceroute information i got using 192.168.15.X ip, 255.255.255.0 subnet mask and 192.168.1.2 getway in my wifi card.

traceroute to 192.18.1.2 failed
> 
Traceroute to 192.168.15.26
Hop		Hostname				IP				Time1	
1		amitava-laptop.local		192.168.15.123		0.225ms
1		no					reply				*
1		amitava-laptop.local		192.168.15.123		2004.159ms

BTW dont worry there is no restriction in internet use in my college. not even torrent download. we've got new admin. so i guess he messed up everything..

---

### Post by taz1234 on 2007-04-28
traceroute uses icmp packets to return the hops info back to your screen.  For security reasions, most router and firewall configurations will not return icmp requests.  This doesn't mean regular traffic can't get out (local or remote).  This is common in colleges so that people can't easily map the internal network topology.

verify with your IT dept the correct network settings first.  Using a class C 192.x.x. address with a 16 bit network mask is rather odd.  A 24 bit mask is generally used for class C networks where the second last octet is used for vlans.  I'm willing to bet that the "15" in the second last octet of your ip is a subnet, not a host address.

---

### Post by joft on 2007-04-28
> **amitava82 said:**
> 
ip: 192.168.15.*
subnet: 255.255.255.0
getway: 192.168.1.2
in windows it pings successfully but not in ubuntu with the same settings.

This configuration **does not make sense**! If you put your PC in network 192.168.15.0 using 255.255.255.0 as subnet mask it will **never** be able to **reach** such default gateway like 192.168.1.2 _without any further routing information_. The TCP/IP stack simply does not know where to send packets, if it wants to send them to your gateway.

> **amitava82 said:**
> here is the route output
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.15.0 * 255.255.255.0 U 0 0 0 eth1


If the routing table looks like this, you _did not specify a default gateway_. This single routing table entry says: packets with destination IP in the 192.168.15.0 network have to be sent out using network interface eth1 - nothing more - no default gateway.

Again, if the above settings work in Windows - which IMO don't make sense - then what is the output of "route print" in Windows? There has to be some routing table entry ... which makes it working (in Windows).

And again: Ask you administrator for the right configuration information.

---

### Post by amitava82 on 2007-04-28
OK I solved the problem adding the following entry to route table
> 
route add 192.168.1.2 eth1

thanks to agark for pointing out to the right direction.. and joft for the explanation :-)

---

