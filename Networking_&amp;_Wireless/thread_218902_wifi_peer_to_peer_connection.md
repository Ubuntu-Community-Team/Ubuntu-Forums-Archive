---
title: "wifi peer to peer connection"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by odysseus.lost on 2006-07-19
Hello,

I want to have a server-client communication between two PCs using wifi. So far I can do that by using an intermediate router with DHCP and TCP/IP server/client programs. What I would like is to take the router out of the loop, in other words have peer to peer communication between the server and the client with static IPs.

Any clues on how to do that?

Cheers.

---

### Post by OpsVentus on 2006-07-19
You have to setup the server as ad-hoc, have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=200409](http://www.ubuntuforums.org/showthread.php?t=200409)
And then connect to this network with the client.

Good luck,
Bart.

---

### Post by odysseus.lost on 2006-07-20
Thanks for the reply. Yup it works by setting my wifi card to ad-hoc mode. In addition to your correct post I also found this one which is the same thing. Adding it in case someone else needs it...
[http://www.ubuntuforums.org/showthread.php?t=93944&highlight=wifi+peer](http://www.ubuntuforums.org/showthread.php?t=93944&highlight=wifi+peer)

---

