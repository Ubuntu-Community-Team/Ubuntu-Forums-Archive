---
title: "dhcp3-server multiple search domains?"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by jcpunk on 2007-05-30
I was interested in setting up an internal network with dns resolution at work.  

In my dhcpd.conf I have
```

option domain-name "mysite.tld";

```
I want to add my internal domain "internal.mysite.tld" to the default search domain.  How would I do this without removing the existing one?

---

