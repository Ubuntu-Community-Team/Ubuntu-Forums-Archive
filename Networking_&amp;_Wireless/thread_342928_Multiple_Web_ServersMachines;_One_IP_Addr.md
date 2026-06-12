---
title: "Multiple Web Servers/Machines; One IP Addr"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by lawtech on 2007-01-20
Is there any way for several machines, each running its own unique-content web server, to share a single external IP address, and have external browsers get to the right server?

Specific situation:

[LIST]
one router
    [LIST]
external address: a.b.c.d
    [/LIST]
    [LIST]
internal address: 192.168.0.1
    [/LIST]
[/LIST]
[LIST]
machine 1 address: 192.168.0.2
    [LIST]
running Edgy/Apache/site1
    [/LIST]
[/LIST]
[LIST]
machine 2 address: 192.168.0.3
    [LIST]
running Edgy/Apache/site2
    [/LIST]
[/LIST]
[LIST]
site1 and site2 have different content
[/LIST]
Desired external access:
[LIST]
http://a.b.c.d/site1 <==> machine 1/site 1
[/LIST]
[LIST]
http://a.b.c.d/site2 <==> machine 2/site 2
[/LIST]
What are the options?

---

### Post by Enverex on 2007-01-20
No, the only thing you can do is use different ports (which are then forwarded by the router to the respective machine).

i.e:
[http://a.b.c.d](http://a.b.c.d)
and
[http://a.b.c.d:81](http://a.b.c.d:81)

---

