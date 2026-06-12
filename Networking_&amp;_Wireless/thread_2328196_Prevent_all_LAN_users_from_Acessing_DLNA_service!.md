---
title: "Prevent all LAN users from Acessing DLNA service!"
date: 2016-06-18
forum: Networking &amp; Wireless
---

### Post by fahid2 on 2016-06-18
Good Day,

I have installed MiniDLNA on my Xubuntu, all is good.
Now I just want restrict my DLNA server to some specific devices only. Reason being there are neighbours sharing the same internet/WiFi, I don't want my personal stuff shared with them.

Although I am not some expert when it comes to Linux but I don't think that MiniDLNA by itself has any such configurations. So my possible option will be define some Firewall Rule in Xubuntu (MiniDLNA Server), which may then allow only some specific IPs or MACs to be able to access this particular service.

MiniDLNA Server by default runs on Port 8200, so I will be looking to restrict connections on this specific port only.

I think it can be represented as something like:
```

Allow from 192.168.0.115 on port 8200
Allow from 192.168.0.124 on port 8200

// or
// Allow from 192.168.0.115, 192.168.0.124 on port 8200

Deny from All on port 8200

```
Even though I may have the idea how to achive what I want, but I have at the moment no clue as how it can be achived. Please Help me get it done.
Note: - there are other services running from same computer and are accessible by all, should remain so.

---

### Post by fahid2 on 2016-06-18
Got it, Solved

from Software Center installed Graphical Interface Utility for Firewal **GUFW**, now all is good to go.

---

### Post by ajgreeny on 2016-06-18
Great. Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by fahid2 on 2016-06-18
Just did it sir. I wanted to mark it as solved but just couldn't find it.

---

