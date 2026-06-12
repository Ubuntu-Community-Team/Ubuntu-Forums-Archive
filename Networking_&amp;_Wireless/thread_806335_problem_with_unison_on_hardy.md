---
title: "problem with unison on hardy"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by hessiess on 2008-05-24
unison doesn't seem to work on hardy.

```
a@a-desktop:~$ unison /home/a/ALL ssh://192.168.1.27//home/a/ALL
Contacting server...
ssh: connect to host 192.168.1.27 port 22: Connection refused
Fatal error: Lost connection with the server
```

---

### Post by kevdog on 2008-05-24
Can you connect just using ssh on the command line?

---

### Post by Antman on 2008-05-25
> **kevdog said:**
> Can you connect just using ssh on the command line?
ssh seems to have the same issue on my pc too
```
ssh: connect to host *hostname*.local port 22: Connection refused
``` I can connect to my fedora box fine however.

---

### Post by Antman on 2008-05-25
> **Antman said:**
> ssh seems to have the same issue on my pc too
```
ssh: connect to host *hostname*.local port 22: Connection refused
``` I can connect to my fedora box fine however.
Oops..looks like openssh server wasn't installed.

---

