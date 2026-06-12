---
title: "Network config troubles"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by dead_donkey on 2008-10-31
The new network configuration tool in 8.10 is great... Except from the fact that it doesn't seem to work properly. 

I've created a new connection using static settings, as I use it to hook up my Xbox via FTP. But when I assign the netmask (255.255.255.0), it seems to change to 24 when I close the settings dialogue.

I am using 64-bit and have upgraded from Hardy, probably the source of my woes...

---

### Post by Iowan on 2008-10-31
I haven't taken the plunge to 8.10 yet - what do you mean "it seems to change to 24"?  255.255.255.0 is the same as /24 for a netmask (just CIDR notation).

---

