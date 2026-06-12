---
title: "Multiple IP blocks on same network setup"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-09-30
Hi all can you help me out here.

I have a router whose IP is 192.168.0.1.  Most of the clients are of the order 192.168.0.x so no problems with them.

There is this one particular machine though that i which to have a totally differnt IP but still be able to browse the web thru the router.  I do not care if it is network browsable. The IP of this machine is 172.16.0.1

I have set it statically with a netmask of 255.255.255.0 and a gateway of 192.168.1.1 and the associate dns servers  but can't get it to browse at all.

How can I make this work

---

### Post by capitalistpiglet on 2007-09-30
ips starting with 127 are reserved for loopback so you cant use it to connect to the network. You should use a different ip range.

---

### Post by sefs on 2007-09-30
Are you seeing things? I clearly have 172.x.x.x. LOL just kidding i made a transposition error .. what i really meant was 172.16.0.1.  I've edited it in the main post to reflect that now.

> **capitalistpiglet said:**
> ips starting with 127 are reserved for loopback so you cant use it to connect to the network. You should use a different ip range.

---

### Post by noob12 on 2007-09-30
Any IP (v4) address with leading octet 127 is a loopback address.  That's not usable for communication from other machines.  Was this address assigned to a non-loopback interface?


If you trying to assign this host an address on the same network as the other clients, then you can go to **System | Administration | Network** and assign it an address of the form 192.168.0.x (preferably choose x so that it is not part of your DHCP pool), subnet mask 255.255.255.0 and gateway 192.168.0.1 .   

You will also need to assign DNS server addresses in the DNS tab in the same panel. If you don't know any you can use the OpenDNS servers at 208.67.220.220 and 208.67.222.222 

If you are not trying to get this host on the same network as the other clients, then you probably need to clarify what you are trying to accomplish.

---

### Post by sefs on 2007-09-30
noob12 note that i made a mistake in typing out my question....

i mean 172.16.0.1 not 127.16.0.1

What i am trying to do is to set a workstation on the network to an IP address that is dissmilar to the other ones there but yet still have it being able to gain inet access.   I had orignally thought that this was possible if i had set it to point to the correct gateway of 192.168.0.1 but no cigar.


to be more specific...

router = 192.168.0.1

computer A = 192.168.0.100
computer B = 192.168.0.101
computer C = 172.16.0.1

all computer have netmask of 255.255.255.0, and dns using opendns

as you would expect computer A and B can connect fine as they are in the same IP block as the router/gateway.

However I have need that Computer C be set out of the address block as dipicted.  So what I am wondering is if its possible to have it set with an IP thats not in the block associated with the router but somehow still have it access the internet thru the router which acts as the gateway.

---

### Post by noob12 on 2007-09-30
Since your 192.168.0 net is in a private address space, there is necessarily NAT going on to the outside world.  The router is probably only capable of doing NAT for the one network it is configured to use.

You'd need something in addition, a second router (or box setup to route) with another layer of NAT , etc.

---

### Post by sefs on 2007-09-30
I was thinking that may something such as a virtual router / software router that does some kind of network trickery exists? I am googling for such...If you know of anything let me know, as I don't have a second router. 

> **noob12 said:**
> Since your 192.168.0 net is in a private address space, there is necessarily NAT going on to the outside world.  The router is probably only capable of doing NAT for the one network it is configured to use.

You'd need something in addition, a second router (or box setup to route) with another layer of NAT , etc.

---

### Post by RandomJoe on 2007-09-30
If you have a Linux box you can pass that computer's network traffic through, you can assign multiple IPs to a single physical connection (they become e.g. eth0:0, eth0:1, so forth) and then set up rules in the Linux firewall to handle routing.  It doesn't have to be in the firewall position for the whole LAN, it can just be one of the computers on the LAN.

But if you really want to separate the one computer, separate physical connections would be best.  Add a second network card to a Linux machine (doesn't have to be your firewall/router) and set up IP forwarding between the two physical ports.  Or you could even use a second DLink/Netgear/whatever firewall box - put its "WAN" port on your current LAN, then set its LAN up for your 172.x.x.x network.

In my house, I use a Linux box for the firewall/router and have three NICs - one to the cablemodem for Inet, the other two for separate subnets.  (In my case, one is wired one is wireless but same deal.)  Iptables rules handle the interaction between the three.

---

