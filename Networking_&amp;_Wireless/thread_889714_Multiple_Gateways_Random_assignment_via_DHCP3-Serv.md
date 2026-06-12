---
title: "Multiple Gateways Random assignment via DHCP3-Server"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by beckols on 2008-08-14
I have two servers, each with a dsl line.  The first server 10.1.1.1 has the dhcp server.  Is there a way to randomly assign all networked computers to one server (10.1.1.1) or the other (10.1.1.2)? My first plan was to put both lines to one computer with load balancing and everything, but it gave me so much trouble, and I've been trying to do it all summer.  This is a temporary fix until I can get it working.  Any help would be greatly appreciated.

---

### Post by bab1 on 2008-08-14
I'm not sure what you mean by
> randomly assign all networked computers to one server...
You can assign an IP address to a specific MAC address via dhcp.  Do not have the same range for both DHCP servers.  Under normal conditions the first DHCP server that responds to a request handles the IP assignment.

Edit: I misspoke and corrected the language.

---

### Post by beckols on 2008-08-14
No there is only one dhcp server (10.1.1.1).  I want it to assign one or the other gateway (10.1.1.1 or 10.1.1.2) to each client that sends a dhcp request.

For example: someone connects the ethernet cable to their computer, the dhcp server gives it an ip address and then assigns it a default gateway of either 10.1.1.1 or 10.1.1.2, so that each dsl line is getting about the same use.  Even just switching back and forth between assigning the two is fine, it doesn't have to be completely random.

---

### Post by bab1 on 2008-08-14
I see.  I don't believe you can easily load balance the GW assignment.  On large Cisco routers (the kind that telcos use) you can do "round robin" assignment of routes.

Edit:  I'm not so sure you want to have multiple GW's on the network.  To use 2 GW's, I think you should be using BGP as the routing protocol.  Most basic routers use RIP or RIPv2.

---

### Post by beckols on 2008-08-15
I'm pretty sure I figured it out.  I set up my network with 2 separate subnets, and declared a "shared-network" in my dhcpd.conf file.  Each subnet had a different "option routers" statement.  I read somewhere that when this happens, all of the ips on the given network are just thrown into a pool and assigned randomly.  It's surprising how little content there is on this feature.  Well, I guess it's not.  It's probably not something that people need everyday :)

Thank you for your help though!

---

### Post by grenadecx on 2011-05-14
I'm sorry for resurrecting this topic, but I'm interested in the very same thing the topic author was and found a solution for.

Anyone that could explain this in a more detailed manner, maybe post an example file of the dhcp.conf?

Why? Because we host somewhat large computer events, where there is no adsl/internet, so we use 3G dongle for this. But using only one gets kinda slow, so if I were able to configure up multiple gateways in the same way the author did, that would be awesome.

---

### Post by redmk2 on 2011-05-14
> **grenadecx said:**
> I'm sorry for resurrecting this topic, but I'm interested in the very same thing the topic author was and found a solution for.

Anyone that could explain this in a more detailed manner, maybe post an example file of the dhcp.conf?

Why? Because we host somewhat large computer events, where there is no adsl/internet, so we use 3G dongle for this. But using only one gets kinda slow, so if I were able to configure up multiple gateways in the same way the author did, that would be awesome.

What do you mean by "somewhat large computer events"?  How large?  What is the network topology?  Will you have 1 DHCP server and want multiple routers (gateways)?  Do all the hosts in the network need to communicate with each other?

You can have multiple DHCP pools with differing DNS, GW, etc.  These are called "shared-network" in dhcpd.conf.  You can read about the configuration [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-dhcp-configuring-server.html#shared-network").

For example a network could use 192.168.0.0/24 for 254 hosts.  The pools could be 64 hosts each with 4 GW's in the network (1 for each pool) or pools of 32 hosts each and 8 GW's.  You can create the pools to fit your needs.  I would suggest that the pools be contiguous.  You need to understand the binary boundaries of the pools as you are in a sense using subnetting of the DHCP IP addresses.  

If you needed a larger amount of hosts you could use the network 192.168.0.0/23.  This would yield 510 hosts or 192.168.0.0/22 would yield 1022 hosts and so on.

---

