---
title: "Router Configuration Questions"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Mizutsuki on 2008-09-04
Hello,
I'm having some difficulty putting together my house network, mainly because I'm so hopelessly inept at networking.  I was wondering if someone might be able to give me a nudge in the right direction (that is, it'd be great if I could find some documentation on home networking/layman's terms tcp/ip)
What I'm trying to figure out is what all of the settings should be for the routers.  I live in a big house with 25 other people living in two separate building, and I'm trying to provide network connections to them all.  I have three Linksys WRT54G units all running dd-wrt (it's just what I had around) so I want for one of the units to receive the connection from the DSL modem/internet, and then I want to have the other two connected to that one.  Let's say the two buildings are called A and B.  A has the modem and the main router.  B has a router with a hard line running to it from the router in A.  I personally live in A, and I want the third router to be for my private wired network (some of my computer don't have wifi card), and I'd like my router to be entirely private (possibly having it's own separate subnet.)  Because I don't have another line long enough, my private router is connecting to Router A by wifi, which I think should be sufficient.
So I'm just having a really hard time filling in all of the fields and understanding what they mean.  What should the WAN IP addresses be, what should the LAN IP addresses be, do I need to worry about NAT?  Can B router act more like a remote wifi AP that doesn't provide DHCP or any services itself and merely passes those requests on the A router?  Will B's wired ports work correctly as wired connections to the LAN provided by A?  What should the gateway on each router be?  Does it matter what the router names are?  Host Name?  Domain Name?  Should router B be connecting to router A via DHCP?  What about DNS?  What does all of this even mean, and why would I set it the way I should set it, and what if it were different?  What is STP?  What is MTU?  Can A and B share a LAN DHCP range?  Is there some document I should be reading so as to not annoy the crap out of everyone on the forums with too many common question?
Thanks so much!

---

