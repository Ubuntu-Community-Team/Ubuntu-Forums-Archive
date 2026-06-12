---
title: "Wireless interface unable to access some ports/protocols?"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by odysseus_nz on 2006-10-21
Hi,

I have both wired eth0 and wireless wlan0 interfaces configured and working well on my laptop, except that when I have wlan0 connected I am unable to access anything on the net other than http/80.  Anything like pop3, ftp/21 or https/445 just times out on me, which is restricting to say the least.  They work fine when I'm tethered to eth0, and work fine from wireless under windows on the same machine, so I'm sure it's not my router. Under my old distro I'd guess that smoothwall or iptables was mis-configured, but as far as I can tell kubuntu doesn't bother with that due to the no open ports policy.

Any clues?

Cheers!

John.

----

Update:  Turns out it was the router, totally bizarre!  I reset the router back to factory settings and re-configured it from scratch, now wireless can access everything again.  What's weird is that I reloaded exactly the same settings...

---

