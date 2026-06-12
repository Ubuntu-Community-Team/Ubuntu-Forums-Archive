---
title: "Route commands with PPTP Client"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Ardee83 on 2007-04-25
Hello all! First post so be gentle :p

I am running the "built in" PPTP client with feisty fawn (network-manager, network-manager-gnome, network-manager-pptp) and am trying to keep all my traffic from being routed to the pptp connection since my work filters traffic through websense. I want all 10.x.x.x traffic to be routed to the VPN and everything else to route through the normal 192.168.1.x. The issue seems to stem from the connection insisting on using the DNS from the VPN or none at all.

If I uncheck "Use Peer DNS" under PPP Options network manager clears out /etc/resolv.conf and I route nowhere. If I check "Use Peer DNS" it adds my pptp nameserver and I can only route through the pptp connection.

If I check "Only use VPN connection for these address" and add in my work's IP range (10.0.0.0/24) I cannot route.

My attempts at changing this with route commands have failed. It doesn't seem to matter where I tell it to send traffic since the nameserve in /etc/resolv.conf is set to the DNS of the VPN.

Ideas? Thoughts?

---

### Post by Ardee83 on 2007-04-25
My God these forums are nuts! :popcorn:

---

### Post by hsnart on 2007-04-27
I've got exactly the same problem. Any help greatfully recieved.

---

### Post by koenn on 2007-04-28
your mistaking dns for routing and vice versa. routing and dns are two separate, very different things. 

I'm using Dapper so I don't know what the pptp tool on feisty looks like, but you should have a look at the tunnel options : 
- you co not want something like 'route everything through tunnel'
- you want something like 'client to LAN' - with a route to 10.0.0.0/24 through the tunnel

to work out the DNS, could you post the contents of /etc/resolv.conf - both what it looks like with and without a pptp tunnel ?

---

### Post by hsnart on 2007-04-29
Ah, my problem is bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37239](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37239)
my dns entry was being removed, so my local browsing etc wasnt working.

---

### Post by hsnart on 2007-04-29
just to be clear. My vpn setup is working fine. But, when NM connects, it removes my DNS entry, so my local browsing etc doens work anymore.

If i add it back in (e.g. by going to system->network->dns and adding it back in there), i'm back in buisness.

---

