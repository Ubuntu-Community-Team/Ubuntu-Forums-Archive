---
title: "Kopete automatically connect upon connection to Internet"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by amar on 2007-06-05
Automatically connect kopete only when knetwork manager is connected to network

I was annoyed with kopete's automatically connect feature on my laptop because it would try to connect when I wasn't yet connected to The Internet. This would throw up some error messages. what i wanted was to connect only when an Internet connection had been established. After searching the Internet for a while and not finding anything I eventually worked out a very simple way to do it so I thought I would put a quick how to up for others lost like me.

The following command will get kopete to connect to the messenger networks:
```
dcop kopete KopeteIface connectAll
```

so I want to run that after connecting to the Internet. So go to
knetworkmanager > options > configure notifications

Then for the event NetworkManager is now connected, pick execute a program

then for the program type
```
dcop kopete KopeteIface connectAll
```

Simple!

---

