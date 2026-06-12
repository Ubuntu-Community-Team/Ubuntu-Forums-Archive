---
title: "Samba by IP only fixed"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by scottishnarn on 2007-03-03
I've been struggling for days to get my samba to work by name rather than just IP number. I've found a few posts about it not working but none of the solutions I found worked. Today I managed to fix it and thought I'd post my solution just in case anyone else ever have the same problem (however unlikely that may be).

First my system. I use a broadband router which assigns IPs in the 10.0.0.0 range, however my linux machine has a static IP. 

The problem, the router sets the netmask to 255.0.0.0 while I set my linux machine's to 255.255.255.0 (I used to be on a 192.168.0.0 ip range). 

The fix, changing my linux machine's netmask in /etc/network/interfaces solved the problem.

A little situation specific but if this error is driving anyone else as mad as it did me there's the fix.

---

