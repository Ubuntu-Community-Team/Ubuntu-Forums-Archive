---
title: "Iptables and nat"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by DaMasta on 2008-10-09
I have a transparent proxy server setup. If it's http stuff, it sends it to port 3128 for caching. Otherwise it goes on to the gateway. The issue arises in that some of us have access to a different network than others and there is no way to segregate the ip's right now since they all show as coming from the proxy server's ip. 

How can I configure iptables to nat any non-http packets as the originating ip?
For example:
My personal computer is 192.168.1.100. My ip has access to the 192.168.2.0 network.
The proxy server is 192.168.1.2.
The gateway is 192.168.1.1.

If attempt to ssh to 192.168.2.10, it gets denied at the gateway because it thinks the proxy is trying to access that network.

I need to send the packets from the proxy masqueraded as my computer's ip so that the gateway will allow it.

**Edit to say that the originating ip is not always the same. We have about 200 machines.

---

