---
title: "NTP Server"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by a_iranbodi on 2007-06-11
Dear All,

I'm going to setup new ubuntu server as NTP server for syncing my routers and servers with.
Accuracy is not importsnt but Syncing is very important to me.

Here is my /etc/ntp.conf

server 127.127.1.0
fudge 127.127.1.0 stratum 10
restrict 192.168.1.0  mask  255.255.255.0 nomodify

but i couldn't sync my servers!
Is there anything wrong with my config file ? 

Alireza

---

