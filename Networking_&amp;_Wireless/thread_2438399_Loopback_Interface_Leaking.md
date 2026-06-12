---
title: "Loopback Interface Leaking???"
date: 2020-03-11
forum: Networking &amp; Wireless
---

### Post by 00nieman00 on 2020-03-11
odds are there are few that have seen this, I'm thinking "glitch" in the  kernel as in my mind this is one of those things that should never  happen - I've reached out to numerous other admin types and comm  engineers and they agree - shouldn't happen
As anyone seen this before? Can anyone explain why?
[lo] is attempting output to multicast DNS - lo shouldn't be trying to talk to anything besides itself

Linux xxx 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Log:
Mar 11 05:46:14 xxx kernel: [   53.352103] DENIED lo Output IN= OUT=lo  SRC=127.0.0.1 DST=224.0.0.251 LEN=73 TOS=0x00 PREC=0x00 TTL=255 ID=21861  DF PROTO=UDP SPT=5353 DPT=5353 LEN=53 

To answer your next question: yes, this comes from creative rules within iptables
Basically, deny all but with the additions of even blocking what should never happen with that said:
rule exist to allow lo to talk to 127.0.0.0/8 but block all other in/out on lo
The result is what you see........lo attempting mDNS

---

### Post by EuclideanCoffee on 2020-03-13
If you want to stop seeing this, you will need to stop the application executing the call. Monitor protocol 5353 to see which application starts the stream. Stop that application from executing, and you won't see the denied message anymore.

---

