---
title: "Firestarter shows port 56810"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by max1e6 on 2010-06-22
My Firestarter GUI shows the following among my active connections:


Source and Destination: 127.0.0.1
Port: 56810, Service: unknown

How can I find out what it is?

---

### Post by cariboo on 2010-06-23
Open a terminal and type:

```
netstat -tnulp
```

it is probably [avahi]("http://en.wikipedia.org/wiki/Avahi_(software)")

---

