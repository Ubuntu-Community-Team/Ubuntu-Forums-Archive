---
title: "Network quirks to work out"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by reader4 on 2008-05-21
Running 8.04-Hardy on my Gateway laptop, Intel 2200 wireless.

I almost never have problems, but twice recently I ran into trouble I could not solve that left me in the dark without internet access.

1. Connected to a wireless network that used some sort of IP routing/browser redirection for authentication.  This has never been a problem, say, in an airport.  On this occasion, however, eth1 (wireless) was enabled and saw available networks.  When I clicked on the one I needed, it would connect, get an IP, but stall.  Starting a browser did nothing to help.

2. Like #1, but this time the network was setup at a company by the guy I was sitting with. It used WPA with a 15-char password. I clicked on the network and was prompted for the password. The connection whirred a while, but then I was asked again. The reconnect didn't "feel" like a "wrong-password" problem - it took several minutes for it to appear - the the problem persisted.

In both cases, I tried what had worked in the past:
Manually:
ifdown eth0 (wired ethernet)
ifup eth1
add default eth1 route
no roaming - manual configuration
restart networking, restart the computer...

It appeared the connection just kept tripping and never moving forward.  I was in a meeting, so didn't run a lot of diagnostics, but was confused as to why the 'check' would show up next to 'wired connection' in the network GUI when eth0 was down.  So frustrating!

Any known problems here, or other things to try next time this happens?

---

