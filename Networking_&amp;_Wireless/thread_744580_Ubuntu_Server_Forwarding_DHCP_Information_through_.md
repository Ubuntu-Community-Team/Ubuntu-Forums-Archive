---
title: "Ubuntu Server: Forwarding DHCP Information through Wireless Router"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Infinite Recursion on 2008-04-03
I currently have a working internet connection with the following network flow:

Internet -> Ubuntu 7.10 Server -> Linksys WRT54G Router -> Wireless Clients.

Currently, the router is providing a DHCP server for all of the wireless clients.  I have my own DHCP already setup on the Ubuntu Server (any device that I directly connect is correctly assigned an IP), and would like that to be used as the 'master' DHCP for the wireless clients.

I must be missing something in the router settings, as when I disable the router's DHCP server, any wireless clients immediately get self-assigned IPs, and are unable to connect to any part of the network (not even the router).

I can continue to use the network as-is, but would like to see how this might be accomplished, as I'm constantly looking for new knowledge that I might be able to use for the future.  While I do know a fair bit about computer administration in general (and learning more all the time), networking is still uncharted territory for me.

I will be happy to provide clarification, or any config files/command output that you may need.  Any help would be much appreciated.

=IR=

---

### Post by pseudo-random on 2008-04-03
As a rule, have only 1 DHCP server. I would use the Router in your case.
2 or more DHCP servers is trouble.

---

### Post by Infinite Recursion on 2008-04-03
I agree with that, which is why I want to disable the router's DHCP.  This is mostly a learning experience for me, otherwise I would be perfectly content to keep the current (working) configuration, with the router as the DHCP.

---

