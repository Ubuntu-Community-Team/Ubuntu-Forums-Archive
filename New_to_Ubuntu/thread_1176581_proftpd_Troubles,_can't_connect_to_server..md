---
title: "proftpd Troubles, can't connect to server."
date: 2009-06-02
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-06-02
When I do sudo this proftpd -td5 it gave me the user.localhost thing on like 10 different things, but when I try to connect to the user.localhost it will not let me, any ideas?

---

### Post by jonobr on 2009-06-02
Is ftp enabled on localhost?

By default, the Ftp dameon/server or service is not there and you have to install.

---

### Post by halitech on 2009-06-02
in a terminal, what happens if you simply use
```
ftp localhost
```

---

