---
title: "connect: Network is unreachable"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by legesh on 2007-06-19
Hi,

I have Ubuntu 6.06 and everything was fine till the last week.
Something happened, because I have problems with networking now.

```
ping 127.0.0.1
```

returns

```
connect: Network is unreachable
```

I need your help!

Thanks.

---

### Post by HubertB on 2007-06-19
Restart the networking subsystem and test it again:
```

user$ sudo /etc/init.d/networking restart
user$ ping 127.0.0.1

```

If there are still no responses, please post your routing table:
```

user$ sudo netstat -r

```

---

