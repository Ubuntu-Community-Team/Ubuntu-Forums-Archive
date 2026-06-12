---
title: "Help Me! Private network to access internet and not"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by darqtanian on 2013-10-10
Okay, I'm kinda confused with networking. Here's what I wanted to do..

I have a (DRBL) Ubuntu server that has 2 NIC.

eth0 - will have access to internet and local network (10.160.1.10/24)
eth1 - will be my private network (192.168.101.254/24)

eth1 is NAT to eth0 so that it will have internet access. I setup a DRBL environment and configured that the (DHCP) IP range between 192.168.101.10-20.24 will be assigned to Linux clients.

What I want to do is.
192.168.101.10-20 = for Linux machines, should have access to internet. (ive already done this)

192.168.101.30-40 = for Windows machines, should not have access to internet but to local network only. if machine will boot as windows it will obtain IP address from this range.

How can I configure this correctly?
Please help me..

---

### Post by TheFu on 2013-10-10
Physical separation is best. 
Describe your routers and switches on the network please.

Routers will route based on rules. You will need to set those.
Basic switches will switch based on MAC addresses and netmasks, enterprise switches can route too.

A basic understanding of networking will be necessary to get this working.  Google "security now ep 25" to start learning.

As to how to split Widnows and Linux machines, I'd use static IPs for the Linux machines and assume everything else is NOT Linux, so it goes to the no-WAN access subnet. I'd try to control that with DHCP reservations - based on MAC. I think you'll need a full DHCP server for this since different networks will be involved. Might need DHCP-forwarding too.  I'm out of my depth here.

---

### Post by capscrew on 2013-10-10
> **darqtanian said:**
> Okay, I'm kinda confused with networking. Here's what I wanted to do..

I have a (DRBL) Ubuntu server that has 2 NIC.

eth0 - will have access to internet and local network (10.160.1.10/24)
eth1 - will be my private network (192.168.101.254/24)

eth1 is NAT to eth0 so that it will have internet access. I setup a DRBL environment and configured that the (DHCP) IP range between 192.168.101.10-20.24 will be assigned to Linux clients.

What I want to do is.
192.168.101.10-20 = for Linux machines, should have access to internet. (ive already done this)

192.168.101.30-40 = for Windows machines, should not have access to internet but to local network only. if machine will boot as windows it will obtain IP address from this range.

How can I configure this correctly?
Please help me..

Certainly not using DHCP as the separator.  DHCP is OS agnostic.  All hosts are peers on a LAN.  With DHCP the client requests an IP address and the server offers one.  The clients configuration has a lot to do with what is in the request but I'm pretty sure the OS is not one of the parameters you can configure.  You could use VLANS but in reality this is not secure separation.    Routers separate networks and there should be no more than one DHCP server per your network (i.e. 192.168.101.0 /[COLOR="#0000FF"]**24**[/COLOR]).  You can have one DHCP server for multiple nerworks but that gets messy.  

If you need to set up separate needs for a group of hosts in a small lab using that network, the simplest thing to do is to statically (via config files) set the IP addressing for the individual hosts.  If you do not assign a gateway IP address, those hosts will have no connectivity with the outside world (e.g in either direction). 

I would not use IP address reservations at all.  Reservations require a DHCP client requested IP address and a response from the DHCP server.  This is not static addressing at all.  

In the end what you want to do can be accomplished easily.  Connect each host in the 192.168.101.0/24 network to an inexpensive unmanaged switch.  Then attach that switch to your Ubuntu Server.  Let the machines that you want to have internetworking connectivity request via a single DHCP pool.  The hosts that you do not want to have Internet connectivity (only  LAN (192.168.101.0 /[COLOR="#0000FF"]**24**[/COLOR]) configure by hand with no gateway. 

If you have more than whatever is painful for you to manually configure then you will need to create 2 subnets with a router between them.  One LAN being  (192.168.101.0 /[COLOR="#FF0000"]**25**[/COLOR].  This would give you a network with 126 usable addresses (.1 - .126) and the other LAN being 192.168.101.128 /[COLOR="#FF0000"]**25**[/COLOR].  The second network would also have 126 usable addresses ( .129 - .254). Put the windows hosts on one net and the Linux ones on the other.   There is more to this than can be explained in one posting, but it gives you an idea of what you are really looking to do.

---

