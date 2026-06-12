---
title: "DNS Theory Question"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by tcpip4lyfe on 2008-07-10
I'm looking for someone who knows a bit about DNS.  I have a couple DNS servers setup at work.  One is a local Dynamic DNS server that maps host names with DHCP addresses. The other is a hosted DNS server on 1and1.com.  When I want to update MX records or A name records on the internet I use the 1and1 DNS server.  What I was wondering is say I create another stand alone Bind9 server and I want to add a new domain called somedomain.com and I set an A name record with an IP address of 208.32.33.33.  *How can I get the my Bind9 server to replicate to another server higher up in the hierarchy?*  Basically I want to add entries on my server and have the rest of the internet know about it.  I assume there is some sort of authentication or trust between DNS servers otherwise any shmuck could just setup a DNS server and have google.com point to 1.1.1.1.

---

