---
title: "program request (saves lifes and time)"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by someoneouthere on 2008-02-05
i want a program running alone or it could be incorporated with iptraf or any similar doing statistic analisys on the inbound-outbound traffic based on the ip(reserving the dns list like iptraf or firestarter) like how many times i was connected with a specific address with which service/programm or i could search for a specific service/protocol on a nice gui or a web interface..
there might be iptraf ,firestarter..... but these are mosty for "live" observation...
if there were a program that could track down all the traffic(once a day) and then merge(the chaos :P ) them in a nice gui with statistics so everyone could manage, control and see if something is actually happening...

is there something like this?

---

### Post by mexpolk on 2008-02-08
I think you can do it with iptables, but you have to deal with manual configuration:

```

iptables -I INPUT 1 -j LOG
iptables -I OUTPUT 1 -j LOG
iptables -I FORWARD 1 -j LOG

```

best!

---

