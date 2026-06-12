---
title: "Ethernet Network Trouble"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by JFASI on 2007-08-28
I have tried to hook a laptop (7.04) up to a Windows XP PC via Ethernet, in hopes of getting them to network and getting internet on the laptop. When I plug the cable into the laptop, windows acquires network configuration, and eventually tells me that the connection has limited to no connectivity. The network looks like this: Laptop -(Ethernet)- Dell PC -(USB)- Motorola Cable Modem. 

Could the problem lie in the fact that the connection to the modem is USB? Or is there something I need to configure before the connection becomes any good? 



I know a properly configured router would probably solve the problem, but I want to try to avoid buying extra equipment. Up until now, it was just this PC and the modem.

---

### Post by Metacarpal on 2007-08-28
If you're trying to connect one computer directly to another, a standard ethernet cable will not work, due to the layout of the connector pins.  There is a special ethernet cable called a "crossover cable" - you'll need one of those.  It means buying one (or modifying an ethernet cable yourself, which generally takes tools, which you'd have to buy), but that's still cheaper than a router.

---

### Post by will71110 on 2007-08-28
> **Metacarpal said:**
> If you're trying to connect one computer directly to another, a standard ethernet cable will not work, due to the layout of the connector pins.  There is a special ethernet cable called a "crossover cable" - you'll need one of those.  It means buying one (or modifying an ethernet cable yourself, which generally takes tools, which you'd have to buy), but that's still cheaper than a router.

You'll also have to tell your box to NAT all traffic.

---

### Post by JFASI on 2007-08-28
What if I were to connect the modem directly to the laptop via Ethernet? I know this works, I just don't know how to get Ubuntu to recognize it.

---

### Post by Metacarpal on 2007-08-28
Thanks for filling in the gaps, Will!

---

### Post by will71110 on 2007-08-28
Well you know...LOL...Just thought I'd add my 2 cents in:lolflag:


Something I had just learned how to do.  Was very frustrating to get it to work but now I think I could almost reproduce out of memory what I did :) (Got a VPN to talk to an internal network)

---

