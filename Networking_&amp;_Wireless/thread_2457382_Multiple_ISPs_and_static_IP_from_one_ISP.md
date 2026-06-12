---
title: "Multiple ISPs and static IP from one ISP"
date: 2021-02-01
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2021-02-01
Dear All,
Question before I make a mistake.
I currently have a wan connection (internet), which hosts 8 ip address (on router A from ISP A), apart from the networking required addresses 1 is used as a default route and the remaining 5 are forwarding traffic (NOT NATTING) to 5 internal devices which are accessible from the internet. Router A has a number of static routes all pointing to an internal ubuntu machine acting as a router for the subnets. All works perfectly.
 
If I wanted to add an addition ISP via router B (much faster connections but no services such as mail DNS , static IPs) as a new outbound default route…
 
I assume I can use the ubuntu router to by default route all traffic via router B, BUT any traffic to from my servers with static ip addresses from router A still to use router A for outbound & access to specific services at ISP A to be touted via router a ?
 
Lastly if ISP B fails, to be able to switch back the default route to ISP A automatically if possible
 
Would this be route commands on the ubuntu server and if so any tips?
 
Many Thanks
Andrew

---

