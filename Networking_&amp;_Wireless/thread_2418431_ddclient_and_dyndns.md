---
title: "ddclient and dyndns"
date: 2019-05-06
forum: Networking &amp; Wireless
---

### Post by pingaan on 2019-05-06
Hey,


I'm not sure what I'm doing wrong here. I have a DynDNS/no-ip account since some time back and I have had it running with Ubuntu before, but I can't seem to get it running now. 
The daemon is active and here's my conf:


```
daemon 600
pid=/var/run/ddclient.pid
ssl=yes
protocol=dyndns2
use=web, web=checkip.dyndns.com, web-skip='IP Address'
server=members.dyndns.org
login=xxx@gmail.com
password='xxx'
xxx.ddns.net

```


Hope this is enough info.


Ragards.

---

