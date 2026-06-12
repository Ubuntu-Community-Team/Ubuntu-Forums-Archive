---
title: "iptables question"
date: 2016-02-29
forum: Networking &amp; Wireless
---

### Post by scojopa on 2016-02-29
I am trying to open incoming connections to specific port from specific network. 

I added the following line to iptables. 

```
$ sudo iptables -A INPUT -p tcp -s x.x.x.x/28 --dport 8332 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```

I rebooted the server but the port shows as listening only for ipv6. 

[HTML]tcp6       0      0 127.0.0.1:8332          127.0.0.1:40527         TIME_WAIT   -               tcp6       0      0 127.0.0.1:8332          127.0.0.1:40526         TIME_WAIT   -             [/HTML]

How can I correct this so tcp is listening on 8332?

Thanks,

---

### Post by SeijiSensei on 2016-02-29
It doesn't appear that the application is listening on an interface that can be reached from your subnet at all, just localhost.  Is the application bound to the machine's network interface?

---

