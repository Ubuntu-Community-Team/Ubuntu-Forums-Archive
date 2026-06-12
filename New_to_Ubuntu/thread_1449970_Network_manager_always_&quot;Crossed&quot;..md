---
title: "Network manager always &quot;Crossed&quot;."
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Laxman_prodigy on 2010-04-08
I installed Debian testing and the network indicator is crossed even if I am connected to internet.

What is going wrong?

---

### Post by zvacet on 2010-04-08
How did you establish connection?Using 

```
sudo pppoeconf
```

maybe?

---

### Post by powder on 2010-04-08
You probably need to comment out your internet connection in /etc/network/interfaces.  See link for details.

[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

---

