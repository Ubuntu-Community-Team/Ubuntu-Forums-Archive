---
title: "DNS Configuration"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by puelly on 2007-03-28
I have been trying for a few days now to setup a DNS server.  I am now trying to do it with bind and I believe that I have it working on the servers loopback address.  How can I link the DNS server to an interface or address on my server?

**Above problem resolved. Apparently Firestarter was blocking requests on port 53**

I have one more problem.  I would like BIND to forward a request for vpn.example.com to a server that has a public static IP address rather than example.com where the website is hosted.  If that's not possible then I would like all requests from users for example.com to be redirected to my server instead of my webhost's.

---

### Post by koenn on 2007-03-28
This requires that you own the domain example.com, i.e. you can not have vpn.your_provider.com pointy to your server unless you convince your provider to delegate control over a subdomain or create an adress record for vpn.example.com pointing to the public address of your vpn gateway, 


If you do own example.com, you can either
1- have the authorative name server for example.com hosted by a third party (your internet provider, your web hoster, someone else, ...) and then they'd just need to create an Address record for vpn.example.com pointing to the public address of your vpn gateway, 

2- make your bind the authorative name server for example.com, and manage all addresses yourself. When you register the domain, the root DNS servers will get a SOA / NS record with name/address = your bind's public address.

---

