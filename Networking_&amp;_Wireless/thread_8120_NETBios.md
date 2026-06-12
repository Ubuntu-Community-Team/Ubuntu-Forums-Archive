---
title: "NETBios"
date: 2004-12-14
forum: Networking &amp; Wireless
---

### Post by gdeswardt on 2004-12-14
Office setup. We are running 15+ computers with windows on a workgroup with no DNS server, but with a DHCP server. My installation is the first (of hopefullly meany) machine on the network that is running Ubuntu the rest all Windows.

When I try and ping another machine on the network by its name 

```
# ping aspenconnect
```

I receive the following error 

```
ping: unknown host aspenconnect
```

But if I do a NETBios Lookup i find the IP Address

```
# nmblookup -R aspenconnect
querying aspenconnect on 193.168.2.255
193.168.2.229 aspenconnect<00>
```

How can fix this that when I try and access a website on the machine I can do it via the machine name and not the IP Address?

---

