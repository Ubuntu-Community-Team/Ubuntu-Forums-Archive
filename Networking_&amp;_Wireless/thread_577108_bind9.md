---
title: "bind9"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by tumandro on 2007-10-15
How do you get bind9 to only open a port on one interface? I'm trying to install it on my router and I don't want the port open on the external interface.

---

### Post by noob12 on 2007-10-16
The global way is **options { ... listen-on ... }**; finer grained controls on **view** definitions if you're using those.

Manuals at [http://www.bind9.net/manuals](http://www.bind9.net/manuals)

---

