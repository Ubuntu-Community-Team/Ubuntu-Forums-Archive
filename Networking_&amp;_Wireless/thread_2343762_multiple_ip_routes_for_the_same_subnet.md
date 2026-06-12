---
title: "multiple ip routes for the same subnet"
date: 2016-11-18
forum: Networking &amp; Wireless
---

### Post by atux on 2016-11-18
hi. i got a server running 16.04 and it has 5 different connections of openvpn as client. it has another 3 as server.
so i am creating a kinda full mesh instance. there is a default route to see a network through a particular route. since i have secondary and tertiary connections, i would like to say that if that route is unavailable then use the next available connection.
all connections sees all networks through different routes.

---

### Post by SeijiSensei on 2016-11-18
Try playing with the metric parameter of route. You can assign priorities to routes so that lower-numbered ones are used first, then up the ladder if a route fails to connect. The "ip route" command, rather than the older, but still supported "route", adds a "preference" option which appears to be an alias for "metric," but I can't tell.  Take a look at [http://serverfault.com/questions/648276/routing-selection-specificity-vs-metric](http://serverfault.com/questions/648276/routing-selection-specificity-vs-metric) which has some good discussion on routing priorities. Linux doesn't include the "adminstrative distance" described in the top-voted answer as one of the commentators notes. So the next criterion is metric.

You can also route on source address using "policy-based" routing with variable routing tables: [http://blog.scottlowe.org/2013/05/29/a-quick-introduction-to-linux-policy-routing/](http://blog.scottlowe.org/2013/05/29/a-quick-introduction-to-linux-policy-routing/)

---

