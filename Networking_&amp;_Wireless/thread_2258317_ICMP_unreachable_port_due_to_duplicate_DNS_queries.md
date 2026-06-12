---
title: "ICMP unreachable port due to duplicate DNS queries"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by steve30401 on 2014-12-26
I recently did a clean install of Ubuntu 14.10.  After that I noticed by my machine was sending ICMP port unreachable messages to my local router.  Upon investigating I found that my machine is sending duplicate DNS queries to both the primary and secondary DNS server.  See tcpdump--

21:55:21.123012 IP 10.115.38.6.25275 > 75.75.75.75.53: 31881+ [1au] A? example.com. (40)
21:55:21.123037 IP 10.115.38.6.25275 > 10.115.38.1.53: 31881+ [1au] A? example.com. (40)
21:55:21.133842 IP 75.75.75.75.53 > 10.115.38.6.25275: 31881$ 1/0/1 A 93.184.216.34 (56)
21:55:21.138871 IP 10.115.38.1.53 > 10.115.38.6.25275: 31881$ 1/0/1 A 93.184.216.34 (56)
21:55:21.138959 IP 10.115.38.6 > 10.115.38.1: ICMP 10.115.38.6 udp port 25275 unreachable, length 92

I'm using dnsmasq as configured by the installation, so that resolv.conf says my server is 127.0.1.1.  My network interface is configured for DHCP and gets 75.75.75.75 and 10.115.38.1 (my local router) as DNS servers.  But as you can see from the timing, the query to the secondary server does not wait for any timeout from the primary query.  The first reply provides the answer, and then the port is apparently closed.  Thus when the second reply comes in the ICMP message is sent.

I tried setting the DNS timeout option to 5 seconds by putting "options timeout:5" into /etc/resolvconf/resolv.conf.d/tail, but that had no effect.  Really that's no surprise, since the request to 127.0.1.1 did not timeout, but I thought perhaps that might make a difference.

Does anyone know why this is happening and what I should do about it?  It doesn't seem reasonable to send a second query until there has been some timeout first.

EDIT:
Found the answer here: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580064](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580064).  Apparently this is as designed and not a bug.

---

