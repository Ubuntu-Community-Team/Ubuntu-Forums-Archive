---
title: "Using bandwidth monitoring tools on an Ubuntu (running as a router with a single NIC)"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by jared20 on 2014-05-09
Hey guys,

Went to bed this morning at 4am with this problem and its driving me crazy. Here is my topology:

------------------------------------------------------------------------------------

_ADSL router (only LAN ports available, does the NAT, etc.):_

IP: 10.0.0.1
Netmask: 255.255.255.0

_Ubuntu Server (running on an ARMv7 device) with a single NIC card:_

IP: 10.0.0.254
Netmask: 255.255.255.0
Gateway: 10.0.0.1

------------------------------------------------------------------------------------

The ADSL router tells my clients to use the ubuntu server as their default gateway. Since the router and the ubuntu server are on _the same network segment_, I found out that I had to disable ICMP redirects (on the ubuntu server) otherwise the traffic just skipped straight to the router. I thought this was the reason why my bandwidth monitoring logs were out (well I think it was partially the reason but I still have issues). I have also enabled "ipv4.forward=1" so it forwards all packets like a router.

Why am I doing this? I want to monitor the traffic destined for the WAN. I want to shape the traffic, I will route port 80 through squid. There are a couple things. Everything is working, except the monitoring of bandwidth. Ok well it is "working" per say (no errors and some traffic seems to be logged) but its a tiny fragment of what it should be.

For example, using iftop on eth0, it shows that my IP (10.0.0.180) is downloading at about 10KBps whereas in reality, I am downloading at about 450KBps while watching it. Bandwidthd shows a total bandwidth utilization of 29MB after I downloaded about 500MB.

***Brainstormed potential problems (need confirmation)***

1) Something that is worth mentioning is that my ARM ubuntu image didnt come with iptables. Would the absense of IPtables affect the bandwidth monitoring like this?

2) Eth0 is essentially the in and out interface. While this might not be a problem for traffic flow (PC's default gateway is the ubuntu box, the ubuntu box's gateway is the router), surely this will break traffic analysis?

***Brainstormed Solutions (need help with these, if they are valid):***

1) I can install iptables when I can connect it to a screen (right now my only access is SSH and apt-get install iptables might block that port). 

2) Three potential solutions. Ideally, I only want to use a single NIC (I want the only USB port on my ARM device to be used for a 3tb HDD). 
[B]
One[/B], mirror only the outbound or inbound traffic on eth0 to a virtual interface (eth0.1) that my monitoring will watch. Not sure if this will work though.
[B]
Two[/B], create a virtual interface (eth0:1) with another IP range (e.g. IP: 192.168.10.1 mask: 255.255.255.0) that my PC's will use as their default gateway. The physical eth0 will have something like IP:10.0.0.254 MASK:255.255.255.0 GW:10.0.0.1. The traffic flow will be from clients (e.g. 192.168.10.50) to ubuntu box on eth0:1 (192.168.10.1) routed to eth0 (10.0.0.254) which will then exit on that ranges default gateway (10.0.0.1). I will need some help with the iptables for this, keeping in mind that i don't want to double NAT (my router is already doing NAT)

However, I only want to do these things if its going to fix my bandwidth monitoring. Like I said, everything else is working lol. If you have any suggestions, anything at all, please speak your mind. I am at my wits end and unfortunately (or fortunately, depending on how you look at it), I will not stop working on this, even if its to the detriment of my health lol (I am OCD like that :P).

Thank you so much guys n gals, looking forward to hearing from you :)

---

### Post by jared20 on 2014-05-10
Hey guys!

Its been a day and I have been working hard trying to solve it but I am still stuck :(

I know this question is a bit TL-DR but I would really appreciate some guidance.

Thanks :)

---

