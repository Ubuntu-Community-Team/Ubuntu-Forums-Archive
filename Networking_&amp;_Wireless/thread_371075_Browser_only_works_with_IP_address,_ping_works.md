---
title: "Browser only works with IP address, ping works"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by Patrick2 on 2007-02-26
DNS, nslookup, dig, and wget work, but browsers (Firefox or Epiphany) only work with a numeric IP address. 

IPV6 is off in the OS and Firefox. I can ping [www.google.com](www.google.com), but can't browse to it or any other URL. The IP address works in the browsers. 

I did a tcpdump to watch the interface, and it looks like neither browser attempts a DNS lookup. 

Other applications Synaptic/apt-get work correctly. I cleaned out my resolv.conf and DHCP repopulates it correctly. 

Any ideas?

---

### Post by Floppyjoe on 2007-02-26
What is in the DNS tab of System/Administration/Networking?
Is it your routers IP? Is your router properly set up to pass DNS to dhcp clients?

---

### Post by Patrick2 on 2007-02-26
> **Floppyjoe said:**
> What is in the DNS tab of System/Administration/Networking?
Is it your routers IP? Is your router properly set up to pass DNS to dhcp clients?


The DNS tab has name servers, set up by DHCP. DNS is not manually set to use the router's IP address, it is dynamically set to use real DNS server, 68.94.156.1 (ns1.worldnet.att.net).

The router seems to be set up properly, nslookup, dig, and wget get results, and non-browser apps (Synaptic, apt-get) also work, hitting the network. W2K likes the router setup. 

From what I can see via tcpdump, the browser never sends out single packet.  If an IP address is used, tcpdump shows traffic, but if a url-name is used, the browser doesn't generate any network traffic. 

It's is as if the browser doesn't understand what to do with a text url. Two different browsers (firefox & epiphany) behave the same. I've logged in to the system in "safe" mode, even tried firefox in safe-mode. Same results.

---

### Post by Shroud on 2007-02-27
Please help I am having this exact same difficulty

---

### Post by Patrick2 on 2007-02-28
One more thing I noticed... this started after update manager ran. 

I've searched the board - a lot of folks are having the same issue. Do we have a bug in the last update?

---

### Post by Patrick2 on 2007-03-02
Bump

---

