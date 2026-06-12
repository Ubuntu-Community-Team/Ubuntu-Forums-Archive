---
title: "One server process on multiple interfaces?"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by DarioD on 2007-09-04
Is it possible to have one server process on multiple interfaces? I'm trying to run an Open Diameter server on three network interfaces. I couldn't find a way to configure it to bind to all three interfaces. So is there a way around it? Perhaps through some sort of IP forwarding?

Thanks.

---

### Post by DarioD on 2007-09-04
Solved it! What I did was enter a new hostname to /etc/hosts with the IP address of 0.0.0.0, and had Open Diameter bind to that hostname.

---

