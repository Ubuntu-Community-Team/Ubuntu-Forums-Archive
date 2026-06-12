---
title: "blocking clients based on ip address"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by pbhj on 2008-06-20
Hi I know there are several ways to do this but I'm looking for the canonical [K]Ubuntu way really.

I'm getting lots of hits from ip addresses in the 24.64.0.0/8 range and would like to block them as a whole (regardless of whether they're hitting any services).

Should I do this from iptables rules (if so how is their a default way to do this in Ubu') or perhaps from host.deny? Some other way?

Cheers

---

### Post by SpaceTeddy on 2008-06-20
i'd use iptables... really. But that is, i speak iptables... So there is no reason for me NOT to use it. 

the command would be
> sudo iptables -s 24.64.0.0/16 -j DROP
if you have a default of Default Rule of ACCEPT.

also, if you want this to load at bootup, put this line into your /etc/rc.local
> /sbin/iptables -s 24.64.0.0/16 -j DROP

btw, i assume that you meant 24.64.0.0/16. If this is correct, the subnet mask should be 24.0.0.0/8 if you need a /8 network. 

hope it helps :)

---

