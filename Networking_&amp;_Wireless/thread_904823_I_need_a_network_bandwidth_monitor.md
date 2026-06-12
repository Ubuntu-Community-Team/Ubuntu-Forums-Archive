---
title: "I need a network bandwidth monitor"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by kelvinator on 2008-08-29
My ISP (Comcast) has just announced that they will be limiting customers monthly bandwidth to 250 GB/Month. I don't think I will exceed that limit but to be safe I am looking for a bandwidth monitor that can keep a cumulative bandwidth usage report. Any suggestions?

---

### Post by babounours on 2008-08-29
take a look at nload maybe

---

### Post by babounours on 2008-08-29
actually gkrellm do it naturally

---

### Post by Billy_McBong on 2008-08-29
I saw that comcast was gonna start caping the bandwidth. I'll have to install gkrellm because i use a lot of bandwidth. :|

---

### Post by mrsteveman1 on 2008-08-29
If you have a router you can put [tomato firmware]("http://www.polarcloud.com/tomato") on it will keep track of use per day, week, month, and it will show you your real time usage.

It can also restrict bandwidth competently per protocol, so you can for instance set a rule to allow all HTTP traffic full speed normally unless a connection goes over some limit like 100MB, then you can have it throttle that specific connection back to 40KB/s transparently. It's quite cool :D

Pics attached

---

### Post by mrsteveman1 on 2008-08-30
I did an example config here for Bittorrent. If you look closely you can see that it is set to put bittorrent connections, regardless of port or IP, into the high QoS class until they use 100MB of transfer, after which the connection switches to lowest.

You can also configure the classes however you want to. I could have set the lowest class to 1KB/s which would effectively stop the transfer after 100MB/s.

You can do the same thing for any protocol, and it seems to be able to do layer 7 protocol detection so you don't have to rely on port numbers.

---

