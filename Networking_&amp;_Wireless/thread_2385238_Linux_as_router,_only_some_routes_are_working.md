---
title: "Linux as router, only some routes are working"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by advancedrouting on 2018-02-18
Machine A is 192.168.0.110 is the linux machine with ipv4 forwarding enabled.

It works with some routes. When I try to route from machine B 178.62.232.231 via Machine A I can see in traceroute that first packet goes to A as expected, but then packet seems to get dropped, nothing happens anymore. If I ping 178.62.232.231 from Machine A it is reachable. There are other route definitions which are working, so I can't really understand whats wrong. There are no special IP-Table Roules, everything is set to default.

If you need further information, just ask, will tell you everything you need.

Thanks for your help.

---

### Post by SeijiSensei on 2018-02-18
> **advancedrouting said:**
> Machine A is 192.168.0.110 is the linux machine with ipv4 forwarding enabled.

It works with some routes. When I try to route from machine B 178.62.232.231 via Machine A 

Route to where?  Another machine in 192.168.0.0/24 or some other address?

---

### Post by advancedrouting on 2018-02-19
Thanks for your reply. The default gateway of machine A didn't know the route, so it couldn't work. Fixed this, no runs.

---

