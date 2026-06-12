---
title: "How to delay pppoe connection at boot?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by cisoprogressivo on 2008-02-11
Hi, an italian W-Gate router/modem. This "modem" in a normal connection gives 2 different IP, one local (192.168.1.xxx) and one public (after a pppoe connection).
I need both the IP because i have an FTP server (so public IP) and a local server (so local IP).
If i type:
```
sudo pppoeconf
```
and i set my pppoe connection to start at boot i get only the public ip.
If i start the connection manually (pon dsl-provider) i get both.
Is it possible to delay the pppoe connection after boot?

Thank you and sorry for my english

---

