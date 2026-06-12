---
title: "How can I share a pppoe internet connection?"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by DjDarkman on 2007-03-24
The question is simple : "How can I share a pppoe internet connection?"

---

### Post by mchan on 2007-04-05
set up a router (Linksys etc)

---

### Post by ZakSmith on 2007-04-05
I'm sure you are looking for more than "set up a router..." :) , so do you already have a router? Give us a little more to work with. Where are you having problems?

---

### Post by hammad1337 on 2007-07-14
Ok, I have the same problem. Here are the details:

I have a linux box running Ubuntu feisty which has a pppoe adsl connection. the connection works just fine.
I have another windows box which needs access to the internet through my linux box.

my "research' on the net provided two solutions:
1. squid proxy
2. ip-tables / NAT/ Masquerading.

the network ip for linux machine is 192.168.0.1 and the (client) windows box is 192.168.0.4.
Please tell me how can i set up either a proxy or NAT...I don't care which.

Thanks :)

---

### Post by hammad1337 on 2007-07-17
For NAT / Masquerade, this works: 
I was confused because I thought that pppoe would be a different interface than ppp, hence it would have a different name (like pppoe0, for example).

---

