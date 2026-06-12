---
title: "[SOLVED] how to go from straight pppoe to router?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by leetrefz on 2007-10-25
When I ran pppoeconf it told me it was changing all this stuff I don't understand. At least:
> start DSL with "pon dsl-provider" terminate with "poff"
now I've got a router. how to undo what pppoeconf did so the router works without a hitch?

---

### Post by az on 2007-10-25
If your ethernet cable is connected to the router, it should start a DHCP connection when it boots without you having to reconfigure anything.  It will try to start a ppp connection, too, but it will fail silently (harmlessly).

If you want to remove the ppp entry, edit the /etc/network/interfaces file and remove the ppp0 stanza.

---

### Post by leetrefz on 2007-10-25
thanks.

---

