---
title: "CUPS 403 error?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by bennis on 2009-03-23
So i have a server install of ubuntu on, guess what, a server! And i'm sshing into it. I installed CUPS and am trying to connect to waiter:631 (get it? a waiter is a server) and when i *do* get a connection, i get a 403 error. I have Apache2 running fine and have torrentflux running fine. Any ideas?

---

### Post by cariboo on 2009-03-23
Try https, you'll get a certificate error, but just ignore it. eg:

```
https://waiter:631
```

Jim

---

### Post by bennis on 2009-03-23
That didn't work. I got the certificate error, but when i added an exception i still got a 403 error.

---

### Post by mcbride_62 on 2009-06-01
Just solved this on my 8.04-2 server.

Added the "Allow all" entries into my cups.conf

<Location />
Allow all
Order allow,deny
Allow all
</Location>

<Location /admin>
AuthType Default
Require user @SYSTEM
# Allow remote administration...
Allow all
Order allow,deny
</Location>

---

