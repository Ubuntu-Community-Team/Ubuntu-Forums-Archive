---
title: "Public DNS question ?"
date: 2014-04-11
forum: Networking &amp; Wireless
---

### Post by rmaultz on 2014-04-11
Got a networking question for anyone Here it goes. I have 2 servers (bare metal). And I want to use google DNs can I configure routing via my router to resolve any local ip (LAN) to resolve to google DNS via entering router broadcast address and have actual router *resolve via internal dns server on router by entering dns address as broadcast ip *example (192.168.0.1) *is broadcast address for router and routers DNS is set to google DNS address *8.8.8.8 and 8.8.4.4.* If you will a pass through

---

### Post by SeijiSensei on 2014-04-11
I'm having a hard time understanding the question, but here goes.

If we're talking about a simple wifi/office router, then you can use the built-in tools to tell it which upstream DNS server(s) to use for name resolution.  By default most of these routers tell the client workstations to use the router as their DNS server during the DHCP negotiation.  The router will also construct a table of hostname<->IP pairings using the hostnames the clients send via DHCP. So, by default, you get the arrangement I think you are looking for.  The router will resolve local names itself and forward any other requests to the specified upstream DNS server.

Now if you are talking about using a Linux box as a router, you'd need to run dnsmasq or BIND9 configured as a caching nameserver.

---

