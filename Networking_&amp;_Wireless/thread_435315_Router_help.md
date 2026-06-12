---
title: "Router help"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by herbster on 2007-05-06
I have a Linksys router and cable modem. If I unplug my router and plug my modem directly to my PC, I can't get the net to work. In Windows, it would just take a few seconds and it would recognize the new connection.

How do I get this to go in Ubuntu?

---

### Post by wiseleader on 2007-05-06
If you set the router as DNS server with router connection, delete this when you're connecting to internet directly through cable modem.

Hope this is helpful

---

### Post by herbster on 2007-05-06
> **wiseleader said:**
> If you set the router as DNS server with router connection, delete this when you're connecting to internet directly through cable modem.

Hope this is helpful

Thanks bro but how exactly do I do that? I don't know where that option is??

---

### Post by wiseleader on 2007-05-07
System -> Administration -> Networking -> login

Find and click the DNS tag, if you see a DNS server entry (for example, 192.xxx.x.x), delete it.

Click OK

Good Luck


p.s. help from a newbie :)

---

