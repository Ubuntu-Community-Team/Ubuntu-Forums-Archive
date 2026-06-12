---
title: "Multiple WAN ip's to Internal nodes"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by adrianm83 on 2007-09-30
I have 4 usable IP addresses from my ISP - i'm wondering if there is a way of routing each IP to a different node on my network

for example i have 1 game server, 1 file server, 1 web server and 1 e-mail server all running on the same machine - which is  a tad old.

I want to split each service up and use dedicated machines. The only way i can seem to do this is via port forwarding using internal addressing, bu i want to make my servers seperate to my LAN. I'm not asking for a complete idiots guide but some help and direction to useful resources and documents would be a great help. I'm planning to use ubuntu on my 4 servers.

I am currently using a linksys WAG54G which is in bridge mode and a Netgear FVS114 as a firewall Router.

---

### Post by RandomJoe on 2007-09-30
It sounds like you want a "DMZ" for your servers.  Basically, you have three separate network segments - the Internet, your internal systems, and the server systems.  

One method of doing this is to have a non-NATting firewall on your 'net connection, behind which are your servers and the NATting firewall for your private network.

Another method, that I've used, is to use a firewall/router with multiple distinct ports (in my case, a spare PC with multiple NICs).  One NIC is Inet, one is DMZ, the third is private LAN.  Be careful configuring your firewall rules! :)  I believe some of the ready-made firewall distros are already setup for this - IIRC, Smoothwall has "Red", "Yellow" and "Green" ports to designate the three different zones.  Been a long time since I looked at those though, I just roll my own.  Unless you have one heckuva net connection, it doesn't take much of a computer to handle this - just about any 'ol spare will do fine within reason.

The first method is (potentially) a bit more secure - you have a separate firewall dedicated to protecting your private LAN, in addition to the protection of the Inet-facing one.  It is also doable with two regular router boxes like your Netgear.  However, you use up another IP - one for the Inet firewall and one for the private firewall in addition to the servers.  The second one eliminates one more hop for the private stuff and reduces how much hardware you have running.  It also only uses a single IP for the firewall(s).

---

