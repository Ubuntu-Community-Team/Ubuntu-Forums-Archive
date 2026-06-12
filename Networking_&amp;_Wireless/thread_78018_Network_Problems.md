---
title: "Network Problems"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by jonbuck on 2005-10-17
Hi I am a newbie and need some help, I have installed Ubuntu and  the networking side is not working correctly. The first thing I noticed was on startup it brings the network ok and quite quickly but fails to get the time from the internet, then once in I can ping any site on the web but it won't load any sites within firefox, it just sits there and then times out. I have checked the network configuration and that all appears to be ok, I have tried DHCP and a static address, both are exactly the same. I tried doing a traceroute which hits my router and then my ISP does another couple of hops and then timesout. I can ping the box from another pc on the lan and likewise I can ping the Ubuntu pc from my other machine, so it looks like the network is fine apart from the internet connectivity.  The PC is a dual boot and if I bring it up in windows mode then the internet is perfectly accessible.

I have a Dell Dimension 4700 connected to a D-Link DSL-G604T ADSL router.

Pointers, ideas, please :)

---

### Post by byourg on 2005-10-17
In the firefox location window type "about:config" (without the quotes), scroll down to "network.dns.disableIPV6 = false", double click this line to change it to "true", now type in a website in the location window and everything should be OK. Hope this helps!

---

### Post by markd on 2005-10-19
I had a similar problem on a new install of breezy (coincidentally same router as jonbuck).  I could ping boxes on my LAN, but not out to Web.  I could see pages other machines on the network had accessed (presumably cached somewhere), but not other websites.

Your fix worked for me, byourg, so thanks.  Can you tell me _why_ it works?

---

### Post by mips on 2005-10-19
The problem lies with the D-Link router.

Some solutions here:
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

