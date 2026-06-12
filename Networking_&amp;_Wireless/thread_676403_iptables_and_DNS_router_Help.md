---
title: "iptables and DNS router Help"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by f7likethekey on 2008-01-23
Hi everybody... tricky problem and I can't seem to find the answer anywhere.  I built a linux router and for some reason whenever I allow DNS out or in it takes 30+ seconds to establish a connection.  Same for the FTP server I'm running.  As soon as I comment out the udp/tcp port 53 it works speedily as can be?

Here is one of the configurations I've tried:

iptables -A INPUT -p udp --sport 53 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT

The only reason I know that it is these two lines is because when they're commented out its fast... but of course then I can't do DNS lookups...

Please help

---

### Post by samaricsm on 2008-02-08
First, you do not need the INPUT for DNS, unless you are hosting a DNS server, in which case it would be over TCP, not UDP.  The INPUT will be a reply to the query you send out and the ESTABLISHED, RELATED should cover you DNS request.

Second, see if adding "-m state --state NEW" after the "--dport 53" doesn't help.  I have the same command as you, with the state condition.  My response is fast.

---

### Post by f7likethekey on 2008-02-09
Thanks a bunch, it seems to be working like a champ.  Not really sure what would cause that but it is fine now...

---

