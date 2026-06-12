---
title: "Connecting to the internet using bluetooth and a nokia 6234 cellphone"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by whitemamba on 2007-12-06
Hi , i'm having trouble setting up a ppp connection , i'm using ubuntu gutsy and 'n asus bluetooth dongle and a nokia 6234 cellphone , i've got the bluetooth setup and it works and i can connect to the internet but i am unable to browse / ping websites. can anyoe help me with this please?

---

### Post by Ndlovu on 2007-12-06
Sounds like it could be a routing problem. If you're already connected to a local network, that will be set as the default route for Internet traffic.

Try typing the following from a terminal:
```
$ route add default dev ppp0
```

and then try ping again. The command above tells ubuntu to send traffic through the modem if it's not sure where else it should go. You can enter the command 'route' without any additional parameters if you want to just see what the routing table looks like at the moment.

---

