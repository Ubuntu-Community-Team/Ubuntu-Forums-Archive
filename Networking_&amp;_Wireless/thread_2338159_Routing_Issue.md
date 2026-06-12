---
title: "Routing Issue"
date: 2016-09-25
forum: Networking &amp; Wireless
---

### Post by uinthas on 2016-09-25
Good Evening,

I have an issue that I have been unable to resolve for my job. I have multiple ubuntu and windows servers, the issue I'm having is when I switch a remote location over from an MPLS connection to vpn linux server does not send the traffic through the proper gateway, this does not happen on windows servers and when I reboot the linux server problem resolved. 

I have all my servers set up the same way, gateway 192.168.1.254 (no additonal routing on the server) so to get from location A (server locations) to location B (remote location) it sends the traffic to 192.168.1.254 (gateway) and 192.168.1.254 sends it to 192.168.1.1 which has a the route sending traffic to location B.  Problem is when I switch location B over to a vpn (location A)192.168.1.254 becomes the gateway to location B, however the linux servers keep trying to send the traffic to 192.168.1.1 even though 192.168.1.254 is the gw.  Window machines do not do this, and when I reboot the ubuntu servers it corrects the problem and it works just fine.  

I have deleted the arp cache even though network B does not even show up in the arp table, I'm not sure how to resolve the issue without a reboot but that is tough to do when you need your serves up and running.  route table is correct I have verified that on all 3 ubuntu servers but they all do the same thing.  Any help would be appreciated.

---

