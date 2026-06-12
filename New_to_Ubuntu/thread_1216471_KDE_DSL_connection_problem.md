---
title: "KDE DSL connection problem"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by ifekaj on 2009-07-18
Recently I installed KDE and I really like how it looks and functionality, but for some reason my DSL connection is not working. When I go to Network Connections, "Wired" tab is empty and "DSL" tab is disabled. This is working in GNOME without any problem. ANyone has any clue? Thanks

---

### Post by ronocdh on 2009-07-19
It's hard to diagnose your problem because your description is a little sparse on the details. For example, are you using a router between your computer and DSL modem?

I would ask in the networking forum, but basically I think the fix will be futzing with **ifconfig** (read the man page) and then incorporating the changes made there into your **/etc/network/interfaces** file.

---

