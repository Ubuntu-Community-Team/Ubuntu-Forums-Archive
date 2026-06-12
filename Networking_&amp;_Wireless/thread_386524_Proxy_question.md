---
title: "Proxy question"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by AAJ on 2007-03-17
Hi, 

My proxy requires username/password, How I can add them when I try to install anything via apt-get.

Regards,

---

### Post by kidders on 2007-03-17
Hi there,

This seemed like something that should have a well-established solution, so I googled your problem, and came up with [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html).

The problem with this solution is that every application you run would be able to see your proxy password, which could very easily be the same as other (more important) passwords. Yuk.

To beat that, you *could* do it this way: (ie set the environment variables explicitly, only when you need it)```
http_proxy="http://username:password@proxy.mydomain.com:port/" apt-get update
```I don't think that's ideal either though. How about:```
http_proxy="`cat /root/.proxy`" apt-get update
```That way, your proxy password wouldn't start cropping up in command histories, etc.

To make life easier for yourself, you could then create a shell script (called eg "apt-get-proxy"), and have apt-get use your proxy automagically whenever you do something like **apt-get-proxy update && apt-get-proxy upgrade**.

How would you feel about that? (Maybe someone else will have a better idea?)

---

### Post by AAJ on 2007-04-19
kidders

Sorry for delay

Many Thanks

---

### Post by kidders on 2007-04-19
Hehe... no problem. :-)

Did you find a nicer solution?

---

