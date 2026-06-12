---
title: "Advanced IPTables Rules Help"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by darrenm on 2006-11-24
Hello all, hoping theres someone here with lots of netfilter experience.

I'm trying to get something working over NAT from one subnet to the next. This is the site topography:

|Local network
|192.168.1.0
 |
 |
{internal_if:192.168.1.254}
Linux IPtables firewall
{external_if:192.168.2.2}
 |
| DMZ:192.168.2.0
 |
 | {192.168.2.3 - network appliance}
 |
 |
{internal_if:192.168.2.254}
Linux IPtables firewall
{external_if:a.public.ip.address}
 |
 |
| [INTERNET]

Hope that makes sense. I need to connect from the local subnet to the network appliance in the DMZ. I have the local subnet masqueraded to the DMZ so the packets source address get re-written. Everything else like web, mail etc works fine so MASQ is working fine.

Capturing some packets I've found that the application that connects to the network appliance goes out on port 15000 UDP where it establishes a connection then comes back on TCP so the NAT forgets the connection.

I am using shoreline as a front end to IPtables to give me a bit easier control, I can get around this problem by adding 
```
DNAT    net:192.168.2.3        loc:192.168.1.22
``` to the /etc/shorewall/rules file.

This forces all traffic from the web appliance to a single PC on the local subnet. But I need to use just pure NAT'ing to make this work rather than port forwarding so I can use more than one PC to access the appliance at a time.

As said, the main problem is that the connection goes out on UDP but comes back in on TCP so the NAT forgets the connection. I know others have got it working. Any ideas?

---

### Post by darrenm on 2006-11-25
bumpety :)

---

