---
title: "port already in use but lsof says not used by anyone"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by sowdust on 2013-10-23
Hello everyone,

I stupidily deleted some webmin files so now I have to re-install it. 
First of all I tried removing it using dpkg but I get a "no package named webmin installed".
So I tried to just re-install it (using dpkg and a .deb downloaded from official website) but when I do so I get 
```
Port 10000 is already in use
```
If  I do ```
lsof | grep 10000
``` I get nothing.

How can I proceed from here?

Thanks,


Mattia

---

### Post by sowdust on 2013-10-24
[SIZE=1](bump?)[/SIZE]

---

### Post by steeldriver on 2013-10-24
Try 

```
sudo netstat -nlp
```

(with a grep for :10000 if you like)

---

### Post by sowdust on 2013-10-24
that did it, thank you very much!

---

