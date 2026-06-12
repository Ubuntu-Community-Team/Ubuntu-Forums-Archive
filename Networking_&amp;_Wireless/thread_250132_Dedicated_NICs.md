---
title: "Dedicated NICs"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by SGFJacobs on 2006-09-03
I Have a server running windows 2003 doing just about everything. I was wonder is there a way to have 2 Nic Card Dediacted with one for Uploading and one for Downloading? Also since i have like 10 Nic cards i can put in the server, would it my sever any faster to have dedicated Nic Cards? For example have a Nic Card Dediacted for FTP port:20. Would this make My FTP Server any faster??

---

### Post by mssever on 2006-09-03
I don't know anything about Win2003 (try a Windows forum...). In Linux, you can set different daemons to listen on different interfaces. For example, apache on eth0, ftpd on eth1, etc.

As far as speed goes, it depends on where your bottleneck is. My guess is that the bottleneck is in the network itself, so having multiple NICs probably won't help you.

---

