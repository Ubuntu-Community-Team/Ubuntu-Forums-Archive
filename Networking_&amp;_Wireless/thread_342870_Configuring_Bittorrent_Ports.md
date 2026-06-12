---
title: "Configuring Bittorrent Ports"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by conor on 2007-01-20
I have been trying to enable forwarded Bittorrent ports on my system.  Using this faq, I attempted with the command ```
iptables -t nat -A PREROUTING -p tcp --dport 6881:6889 -j DNAT --to-destination 192.168.1.2

iptables -A FORWARD -s 192.168.1.2 -p tcp --dport 6881:6889 -j ACCEPT
```

Previously, I could then run nmap and the ports would 'magically' open up.
Now (after a reload) the nmap command tells me that my local host is down.  When I attempt eh -P0 flag, as suggested, nmap hangs.  

There must be some way to utilize the forwarded ports without nmap.

I am on a local network where I am not the administrator of our router and therefore cannot determine the opened ports on the router.  I am ALMOST certain that they are open.

Can somene please walk me though:

1) How to tell which ports are open
2) Open any closed ports between 6881:6899 or between 10000:60000
3) How to make sure that the forwarded ports are enabled

Thanks in advance
Conor

---

