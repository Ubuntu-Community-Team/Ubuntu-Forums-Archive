---
title: "IPv6 Problems?"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by jenic on 2006-12-23
I've searched, I'd say a fair amount for answers but I've come up empty handed each time. I don't know how long its been going on, having installed logcheck just a few months ago but I am getting a lot of this:
```
Dec 22 22:35:01 jenic java: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:35:03 jenic java: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:35:12 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:36:16 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:36:17 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:37:59 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:42:38 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:43:58 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:45:18 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
Dec 22 22:59:01 jenic x-session-manager: gethostby*.getanswer: asked for "jenic.gateway.2wire.net IN AAAA", got type "A"
```
And it just goes and goes. For w/e good it does heres ifconfig as well:
```
eth0      Link encap:Ethernet  HWaddr 00:11:2F:25:0F:42  
          inet addr:172.16.1.36  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::211:2fff:fe25:f42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:416426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423086 errors:1 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:208171520 (198.5 MiB)  TX bytes:186678919 (178.0 MiB)
          Interrupt:193 Base address:0xa000
```
I can understand some of that but I'm no guru so if that helps any, great. I am guessing its a DNS problem by the AAAA and A. So my question would be is there something wrong with my network? (2Wire/SBC aDSL) With how this computer is handling IPv6 queries? Google brings up some mention of this very problem on a few red hat mailing lists and in usenet, but no one responds to them with a viable solution, or at all. Hopefully I will fair better. Thanks in advance.

---

### Post by pavulon on 2007-04-10
I just read your post about your problems with the error message.  I too have a 2-wire router with AT&T DSL.  I've been in the process of moving over from my old network to my new one.  I just started seeing this same error message recently.  I was looking through the search engines hoping to find an answer myself.

If you have found an answer I would appreciate it if you point me to the right direction.

Thank you in advance.

Jim

---

### Post by nautilus on 2007-04-15
ipv6 compatible nodes will always prefer ipv6 addresses over ipv4, since it's part of the standard.

from what i can see, it's looking first for AAAA (ipv6 address) records, and falling back to A (ipv4 address) records.

is it causing problems, other than an overinterested logging daemon?

---

