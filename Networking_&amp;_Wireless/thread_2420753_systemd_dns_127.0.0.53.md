---
title: "systemd dns 127.0.0.53"
date: 2019-06-10
forum: Networking &amp; Wireless
---

### Post by tendouser on 2019-06-10
is there any benefit using 127.0.0.53 and not an external dns server??

---

### Post by chili555 on 2019-06-10
The reference to 127.0.0.53 means that dnsmasq is running on your system. The advantage is that dnsmasq accepts DNS queries and either answers them from a small, local cache or forwards them to a real, recursive DNS server. In other words, dnsmasq will cache the address of each visited site. When you again visit, for example [www.ubuntuforums.org](www.ubuntuforums.org), the system needn't query an outside DNS nameserver, 8.8.8.8, for example; it already knows the answer:  91.189.94.16. The whole process is faster.

Of course, your system has fallback DNS nameservers available. You can find out which with:  ```
resolvectl status | grep DNS
```

---

### Post by tendouser on 2019-06-10
so why always ISP force ms windows OS to use their dns servers.... I have noted yellow exclamation mark in the task bar wifi icon when I customize them???

---

### Post by chili555 on 2019-06-11
> so why always ISP force ms windows OS to use their dns servers.I couldn't speculate why. I suggest you ask on a Windows forum and ask your ISP.

Many of us on this forum, including me, haven't used Windows in many years.

---

