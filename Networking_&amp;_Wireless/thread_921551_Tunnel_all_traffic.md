---
title: "Tunnel all traffic"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Anthron on 2008-09-16
I'm trying to figure out a way to tunnel all traffic from my ubuntu install through a ssh tunnel. I was wondering if there was one, simple, central place to do this, or if I need to go around application to application and configure them independently.

Will the Network Proxy Preferences [gnome] dialog box accomplish what I want? From what I've been reading, it is not inclusive of all traffic.

---

### Post by timcredible on 2008-09-16
tunnels are point to point.  are you trying to use a tunnel to different places?

---

### Post by Anthron on 2008-09-16
A Dynamic tunnel, or a SOCKS proxy. Maybe I should have been more specific.

ssh host -D port

Can I set up a route that will route all traffic through a SOCKS proxy?

---

