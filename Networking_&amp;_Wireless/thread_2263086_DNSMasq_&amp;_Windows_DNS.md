---
title: "DNSMasq &amp; Windows DNS"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by nigel11 on 2015-01-29
Is there any way to get DNSMasq to update a windows DNS?

I have inherited a network running a DNSMasq as Primary DNS and a windows 2003 server as Secondary.

The DNS records in the windows server are very out of date (same IPs mapped to different PCs several times), although scavenging is running.

It looks like the windows is never notified by the DNSMasq. Anyone know how to achieve this?

Cheers

---

### Post by SeijiSensei on 2015-01-29
What server is handling DHCP?  If it's Windows, make it the primary.  If it's a Linux box running isc-dhcp-server, then you can install bind9 on that box and tell dhcpd to update the DNS when it hands out a new address.  Then make the Windows DNS server a slave to the box running dhcpd/bind.

---

### Post by nigel11 on 2015-01-29
The DNSMasq is a DNS and DHCP server in one and running as primary DHCP, windows DHCP is installed but turned off.. I have a large workload and was hoping to avoid having to replace the DNSMasq with BIND. 

If DNSMasq really isn't going to play ball I would switch to BIND. Would it be possible to install BIND on the same machine, move everything in and them just active BIND/Deactivate DNSMasq or is it more complicated than this? does BIND really work well with Windows DNS?

Cheers for your help

---

### Post by SeijiSensei on 2015-01-29
I've set up the reverse arrangement where the Windows DNS server is the primary, and a Linux box running BIND the secondary.  I would imagine the reverse would work just as well, since zone transfers are pretty standard.

I've never used dnsmasq except on Ubuntu workstations.  I don't know how well it works as a standalone DNS server.  On the Ubuntu desktop, it acts as a proxy to remote nameservers.  

If there is a way to dump a standard zone file from dnsmasq, then perhaps you could do that and use the result in BIND.  I've never configured the dhcpd/bind interface in those programs because I've never had the need.  There are quite a few [howtos]("https://www.google.com/search?client=ubuntu&channel=fs&q=dhcpd+bind+integration") out there on the subject.

---

