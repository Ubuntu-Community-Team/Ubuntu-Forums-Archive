---
title: "Dual-NIC behavior"
date: 2017-04-23
forum: Networking &amp; Wireless
---

### Post by micahtangelo on 2017-04-23
Hey all,

I just recently struggled through some trouble with getting my 14.04 machine to connect to my network correctly for more than 1 boot cycle. I'm hoping to get some clarity and understanding of some behavior I was seeing. 

First, the machine is a brand-new TRT2 server from SuperMicro. It has dual 10G Intel NICs onboard. When I had both of these plugged into my switch, it appeared to work just fine - no trouble getting IPs or routes, and I didn't concern myself with how the network was behaving at all. I set a static DHCP lease on my router for one of the NICs (the other wasn't showing up in the UI). The next day, after a reboot, no Internet. I struggled for quite a while until finally getting to the point that on every reboot, I'd delete the default route and tell the system to set a new one, and it would just work. I couldn't get it to work across reboots with both NICs active. So I altered /etc/network/interfaces and disabled one of the NICs, and set a static IP and route through the other one, which is working OK. 

However, defaultly I have no DNS servers for some reason. Despite having a dns-nameservers entry in my interfaces file. I have taken to manually entering the DNS servers in resolvconf's base file. 

So my questions are: 

1. Is it expected that having two NICs connected to the same network at the same time would cause trouble with routing, and if so, where is the documentation showing how to properly configure for this use case? I searched as well as I could and read a ton of forum posts, but nothing really about this (what I feel like must be a pretty common use case?)
2. Anybody have an educated guess as to why the DNS servers in my interfaces file are being ignored? Is adding the DNS nameservers to the base file really the only way to solve this problem?

Thanks kindly!

---

### Post by TheFu on 2017-04-23
No idea about the dns-nameservers issue. Sorry.

Yes, it is an issue to have 2 NICs on the same subnet unless you handle things manually. There is nothing "automatic" about using 2 NICs on the same subnet.
Is there a virtual IP that is for failover?  
How are you dealing with the routing?  
1 of them needs to have the default route, right?  
Are you using different priorities/metrics?  
What about the gateways? 
Are they the same?  
Did you plan to bond the interfaces together to get more throughput?  
Does your switch support bonding?  

Your settings have to answer some of those questions.

---

