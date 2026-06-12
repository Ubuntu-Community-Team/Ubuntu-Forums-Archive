---
title: "how can i view network clients?"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by aztektum on 2007-11-14
I've used Linux a bunch at home (well before Ubuntu existed), but I'm trying to use it at work and really don't have experience using it on a business class network.

On Windows I use this thing called Look@Lan which gives me a relatively real-time look at clients connected to the network. It lists (among other things) hostname, IP, OS... Is there a similar app or some hack I can use to do this on Linux?

I know about nmap but I'm not sure that's the right tool.

Ideally I can see hostname, IP, MAC address (not sure look@lan lists that)..

Thanks.

---

### Post by kidders on 2007-11-15
Hi there,

I'm sure you could hack something together reasonably quickly to spit out the details you mentioned, if you're not too fussy about making it pretty. Since you mention nmap, how about something like...```
for f in `nmap -sP 192.168.1.0/24 | grep "appears to be up" | sed 's/ [^(]* (\([^)]*\))/ \1/' | cut -d' ' -f2`; do nmap -T4 -A $f; done | less
```Perhaps that's overkill but you get the idea. If your network is big, you'll have to be careful what you ask nmap for, and _how_ you ask for it, so your scan doesn't take too long.

Other handy places to find information about your network include things like /proc/net/arp (for MAC addresses).

---

