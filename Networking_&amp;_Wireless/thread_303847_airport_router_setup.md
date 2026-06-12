---
title: "airport router setup?"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by greg.hagen on 2006-11-20
I did some searching, but I was unable to find any way to set up an apple airport extreme base station under Ubuntu. I can connect just fine... AFTER it has been set up with the airport router config thingie in mac os x. Am I missing something? Any ongoing projects that I'm not seeing? I'd really like to change settings without borrowing my girlfriend's macbook.

Thanks in advance.

---

### Post by spd106 on 2006-11-21
All I could find is this page [http://docs.info.apple.com/article.html?artnum=106858](http://docs.info.apple.com/article.html?artnum=106858).

About 2/3 of the way down it suggest an ip configuration to connect to it.
```

IP address: 192.42.249.15
Subnet mask: 255.255.255.0
Router: 192.42.249.13

```

So I guess it defaults to 192.42.249.13, maybe using the avahi-service-discovery app to detect bonjour devices could help.

---

