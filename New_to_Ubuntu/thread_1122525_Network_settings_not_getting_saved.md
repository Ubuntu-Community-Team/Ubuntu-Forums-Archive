---
title: "Network settings not getting saved"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-04-11
Dear All

I use Ubuntu 8.10

My network settings do not get saved.

After every restart I need to provide the details again.

I checked the file /etc/network/interfaces but it does not have entry for eth0

---

### Post by spiderbatdad on 2009-04-11
use gedit or nano as root and edit the file, to add auto eth0,
I assume this is for a wired connection.```
gksu gedit /etc/network/interfaces

auto eth0
```

---

