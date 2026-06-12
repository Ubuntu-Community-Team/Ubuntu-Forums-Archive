---
title: "Unable to save gateway address"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by NubKnacker on 2006-10-14
I have a Netgear wireless router with DHCP disabled. I just downloaded Edgy and installed it on my laptop, thanks to the wonderful work by the ubuntu team edgy detects my wireless card (Broadcom 4311) automatically, something which dapper didn't do.

However, I have a new problem. Edgy doesn't seem to like my gateway, 192.168.1.2 at all. I tried to connect my wireless but it just wouldn't save my gateway address and I kept getting, "network unreachable". I gave up on that within an hour and decided to install GTKwifi to make my life easier. I pulled my LAN cable and plugged it in, configured my wired connection accordingly, still no internet. When I went back into my config I noticed that the gateway address was not saved. Is anyone else having this problem or am I doing something wrong here?

I'd really appreciate it if someone could tell me what I can do next, I have been trying to get wireless working on my laptop for a couple of weeks now with no success.

Thanks in advance.

---

### Post by apjone on 2006-10-15
looks like you may have /etc/network/interface set up for DHCP. can you post it here for us

---

### Post by ricks1950 on 2006-10-16
I had this issue in Edgy for a while as well -- it got solved by an update.

sudo route add default gateway 192.168.(your router address)

This will get you on the net, get your updates and all should be well.

---

### Post by Subbu.exe on 2006-10-17
> **ricks1950 said:**
> I had this issue in Edgy for a while as well -- it got solved by an update.

sudo route add default gateway 192.168.(your router address)

This will get you on the net, get your updates and all should be well.
Thanks.. I Had the same Problem too, that Solved it.. :)

---

