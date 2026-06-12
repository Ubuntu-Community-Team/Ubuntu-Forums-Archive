---
title: "Forward Traffic Based on Subdomain (Like Port Forwarding) - Is it Possible?"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by awells527 on 2007-09-04
Hi, I have an Ubuntu 7.04 server setup with working DNS, firewall, and DHCP.  I have it setup as a typical router with two network interfaces - one for the Internet, and the other for my internal network.  It's functional in getting the Internet available to the network.  I also have basic port forwarding working.

My problem is that I want to forward a subdomain to a specific computer on my network.  If I have [www.example.com](www.example.com) pointed to my server, I know I can forward [www.example.com:480](www.example.com:480) to a computer on my network using port forwarding, but is it possible to forward sub1.example.com to a computer within my network?

I did see the threads on using mod_proxy for Apache, but I would like it to work for all ports because I want to use apache, ftp, etc on this server running under the subdomain.

---

### Post by netztier on 2007-09-05
> **awells527 said:**
> I did see the threads on using mod_proxy for Apache, but I would like it to work for all ports because I want to use apache, ftp, etc on this server running under the subdomain.

This is going to be quite difficult. 

If you want to go the "simple" port-forwarding way, all the intelligence of which-computer-to-forward-to must be based on what significant information is available during the three-way-TCP handshake. And that, I'm afraid, is nothing more but an **IP destination** address and a **TCP destination port** number in the incoming IP packet containig a TCP SYN. Since [www.example.com](www.example.com) and [www.sub1.example.com](www.sub1.example.com) most probably will resolve to the same (single) external IP address of your router, there's no way to distinguish one incoming TCP SYN to port 80 from another. 

If you want to base your forwarding on what *inside* the TCP payload, the intelligence must be placed on the system that first gets to see the actual payload of the incoming (web) request. This information is only available *after* the inital TCP handshake, in form of the URL the client has requested - so you need some device doing that job: a proxy. If you have only one single external IP address, I'm afraid it's not going to work without one. 

The Proxy of course must be able to understand any protocol you want to run - http, ftp etc, but that should be possible for the most common services. For SSH, you're better off doing individual port forwardings for each interal host - an SSH session is probably going to bark at you because of a possible Man-In-The-Middle attack if you proxy it. It might even work with SSL, but you'll have to terminate the SSL tunnel at the proxy and if needed build another SSL session to the real server inside - which could remain plain http also.

You could do it with a "Layer 7 Switch" or "Load Balancer" device.  These a some form of proxy function, in as much as they answer the incoming TCP-SYN with a TCP-ACK on behalf of the actual host - without even knowing which one this is going to be. When they afterwards see the actual request coming in, they simulate the TCP handshake towards the real host (since now they know which one it has to be) and then "connect the loose ends" of the TCP connections. This takes some clever on-the-fly rewriting of TCP source port numbers and TCP sequence numbers - truly advanced stuff. I don't know if there's a software for Linux that does this.

If however your Internet access supports the use of multiple external IP addresses, things might become more interesting, since you can distinguish incoming requests by their destination IP address - and you might be able to solve it all with port-forwarding.

best regards

Marc

---

