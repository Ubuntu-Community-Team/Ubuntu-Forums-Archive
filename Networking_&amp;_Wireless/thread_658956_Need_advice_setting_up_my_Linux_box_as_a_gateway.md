---
title: "Need advice: setting up my Linux box as a gateway"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by bsh on 2008-01-05
Hello
i'd like to set up my linux box as a gateway for the local network.
the network is: cable modem -> router, then on the router there are 2 pc's, one is my linux box which runs 24/7, and the other is my windows pc.
because my linux box acts as a file server, a torrent seed box, an ftp server, etc. it uses the internet bandwidth heavily, and my router has no qos support, so my windows pc's internet lags.
i want to get to the internet through my linux box (as a gateway) and use my router as a dns server.
since i can set up a friendly traffic control que (sfq) which shares bandwidth equally to all concurrent connections, it would be good to pipe all windows traffic through the linux sfq que.
i need some advice on how to make this.
thanks in advance

---

### Post by Predator[23rd] on 2008-01-05
this should help:

[https://help.ubuntu.com/7.04/server/C/ip-masquerading.html](https://help.ubuntu.com/7.04/server/C/ip-masquerading.html)

---

