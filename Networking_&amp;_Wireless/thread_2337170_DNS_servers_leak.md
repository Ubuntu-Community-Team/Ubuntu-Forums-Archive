---
title: "DNS servers leak"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by reese1379 on 2016-09-15
I've configured my modem to access two local DNS servers, yet this [site]("https://ipleak.net/") reports my DNS as '216.66.88.98 United States - California'. And this [site]("https://www.dnsleaktest.com/") reports "The servers identified above receive a request to resolve a domain name (e.g. [www.eff.org]("http://www.eff.org")) to an IP address everytime you enter a website address in your browser." I am confused what gives?

[IMG]https://cdn.pbrd.co/images/3lccwETXF.png[/IMG]

---

### Post by SeijiSensei on 2016-09-15
I don't know what you mean by "configuring your modem" to use two local DNS servers.  If you have a DHCP server on your network, you need to configure that to hand out the local DNS servers when client workstations request an IP address.  If you use static addressing, you need to configure their DNS servers statically as well.

If that's what you have done, we can move on to other possibilities.

---

### Post by Keith_Helms on 2016-09-15
I wouldn't worry about it too much.  You connect to the internet through an ISP and that ISP assigns an externally visible IP address to your cable modem/DSL modem or whatever.  The site you're looking at is just taking that external IP address and doing some kind of a lookup to see what DNS server is used for it, which points back to the DNS servers at your ISP.  Internet sites have no visibility to DNS servers inside your local network.

---

### Post by reese1379 on 2016-09-15
I changed the default DNS provided by the ISP to see if I could speed-up DNS lookup. I chose the nearest as reported by namebench. There's a setting on the modem to manually enter two DNS IP addresses. On the desktop I set DNS servers to 192.168.1.1. I'm just curious as to why those sites report [COLOR=#000000]216.66.88.98 as my DNS server. What happens when you do the test?[/COLOR]

---

### Post by Keith_Helms on 2016-09-15
When I pulled up that ipleak.net site it reports my dns server as 205.171.253.212, which is owned by my ISP Century Link.  The dns server that Century Link actually assigned to my system through dhcp is 205.171.3.25 which is close, but not an exact match.

Just to see what would happen, I edited my wifi connection, changed the IPv4 setting to Automatic (DHCP) addresses only, entered the google dns servers 8.8.8.8 and 8.8.8.4, and then bounced the connection.  NOW that ipleak site reports 24 addresses under DNS address detection.  They all seem to start with 173.194 or 74.125.  When I clicked on one of them it says Mountain View, California which just happens to be where google's headquarters are.

Sooooo, my guess is that 8.8.8.8 and 8.8.8.4 resolve to a round-robin list of actual servers under the cover.  I'm curious how ipleak somehow knows what dns servers I have configured internally.  Must be some http voodoo I'm not familiar with. :D

EDIT:  I poked around and came across the feature called "Round-robin DNS" and also RFC 1794.  So you may enter a single IP address as a dns server, but that address may get resolved to a list of addresses by the dns system.

---

### Post by SeijiSensei on 2016-09-15
I have a local DNS server on my network with a private address in a 192.168 subnet.  When I run the test at dnsleaktest.com, it reports my router's external IP as my DNS server.  That would be true if I were using the router as my DNS server, which is pretty common, but I'm not.  So it, unsurprisingly, has no way of determining what DNS server I'm actually using.

---

### Post by reese1379 on 2016-09-16
Interesting, thanks for both your responses.

---

