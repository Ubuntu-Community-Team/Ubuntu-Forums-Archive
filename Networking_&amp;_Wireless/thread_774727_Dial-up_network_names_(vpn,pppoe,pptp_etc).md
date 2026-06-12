---
title: "Dial-up network names (vpn,pppoe,pptp etc)"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Holy Cheater on 2008-04-29
Example: I have 2 PPTP interfaces: provider1 and provider2.
So I bring up provider1->ppp0, then provider2->ppp1.
If I bring up provider2 first - it will receive ppp0 name?
If the answer is "yes", then here is the question: Is it possible to make connection names static?

Packages for iface mgmt: pppd, pptp-linux.

---

### Post by SpaceTeddy on 2008-04-30
if you go via network manager, use the PPP-Option in the konfiguration Window of the VPN and specify the unit number - i.e. put in 

```
unit 3
```

if you always the the device to be ppp3

NOTE: i have never done this before not ever tried it out. I got the option through the the manpage (searched for interface) and then checked if one can pass options to pppd when invoked via network manager. 
In other words - this is just a guess !

hope it works :)

---

### Post by Holy Cheater on 2008-05-01
Big thanks, that parameter also exists in pppd (I don't use NM).

---

