---
title: "ip forward"
date: 2005-04-01
forum: Networking &amp; Wireless
---

### Post by nahkapaavali on 2005-04-01
So i´m trying to share my Internet connection in Ubuntu, but i´m kinda lost here. I´m missing exact command which let my other machine use Internet. I´ve tried commands like:
[B]iptables -A FORWARD -i eth0 -o eth1 -m state \
--state ESTABLISHED,RELATED -j ACCEPT[/B] 

and
**iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT** 

then it says: **Bad argument 'state'**  :-( 

Are these commands for other versions of iptables than the one in Ubuntu 1.2.11.10?

---

### Post by alastair on 2005-04-01
I won't go into IPtables low-level detail here, but if you INSIST on writing rules manually, then you would be best looking around on the web for the many resources on netfilter/iptables - both reference docs, howto's and lots of user script setups.

If I was you, I would install something like Shorewall (package : shorewall) and have a look at the excellent docs on how to configure it at :

[http://www.shorewall.net](http://www.shorewall.net)

It is a more abstract (but powerful) layer above netfilter and well worth looking at. It lets you do what you want more straightforwardly.

---

### Post by fdoving on 2005-04-01
It's pretty easy.. if you just want to share.. 

masq.sh
```

#!/bin/bash
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE


```
if your output interface is eth1.. change to fit your setup.. 


I can recommend guidedog (sharing) and guarddog (firewalling), if you want gui setup utils. Both are installable from the universe repository.

---

### Post by nahkapaavali on 2005-04-02
Thanks for the replys.

I thought that if i manually configure the firewall and learn from networking at the same time. 
I think i will look fot these guis to ease me on this.

---

### Post by fdoving on 2005-04-02
[QUOTE=nahkapaavali]Thanks for the replys.

I thought that if i manually configure the firewall and learn from networking at the same time. 
I think i will look fot these guis to ease me on this.[/QUOTE]
 Take a look at [http://www.tldp.org](http://www.tldp.org)
Very nice site with loads of information just waiting for you to learn :)

---

### Post by nahkapaavali on 2005-04-03
[QUOTE=fdoving]Take a look at [http://www.tldp.org](http://www.tldp.org)
Very nice site with loads of information just waiting for you to learn :)[/QUOTE]

Jeesh. There IS a loads of information to learn. :-) 
I knew the site but never actually went there to search for something. 
Thanks mate!

---

