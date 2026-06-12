---
title: "Probes penetrating my router/firewall (shorewall)"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Rizla on 2008-06-04
Hey guys,

I didnt really know where else to turn to for a quick second opinion.

While troubleshooting an FTP issue with Shorewall on my home LAN I noticed that there were a ton of packets being dropped by my net2all policy.  Which is a good thing.

I hadnt checked my logs in a while becuase i've been lazy, but low and behold i was seeing continuous probing from Chines and Canadian sites.

TO get an idea of my setup.  I have my Westell 327W wireless/router/firewall that give me my WAN ip.  I have a restrictive firewall policy on it that only allows the services that i've defined to exit/enter my network.  

Only on port is being forwarded internally (SSH on a nonstandard port *a high port number*).  

Then from there i have a cable from my westell router feeding into my linux router/firewall thats running shorewall.  I have multiple nics in it to segment my internal networks (one for me, another for my roommates, and another for wireless).

So i have "two firewalls".  One via Westell and my second internall via my shorewall firewall.

Problem is that these probes are penetrating through the Westell router and hitting the "outside" interface on my linux router.  They're being dropped which is good, but they shouldnt even make it that far.

For the sake of seeing whether I could replicate the scenario.  I hopped on an external network (neighbors wifi)and fired up an nmap probe of my WAN ip.

the initial scan turns up nothing but when i passed the -PN option it took its time going through the ports.  I was monitoring my shorewall log as this was happening and saw that all of nmaps probes were going through my westell firewall.

I know i'm being overly critical of this, but isnt that the point of a firewall to block erronious traffic from coming in?  

Luckily the ports that i'm constantly being probed are on UDP 1026-1028 are ms-sql server ports that I currently dont have running.  I've noticed a smattering of other ports being probed.. TCP 8080 and some other ones..

Anyone else experience a similar issue?  All i have to say is, i'm glad I'm "double bagging it" with my linux firewall.

---

