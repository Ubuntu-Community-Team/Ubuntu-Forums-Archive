---
title: "is e1000 driver in gutsy 7.10?"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by candtalan on 2008-01-18
I am a volunteer helper for a couple of Dell Vostro low end machines and with feisty 7.04 I had to get network drivers arranged specially for the wired connection. Does anyone know if these drivers are now included in gutsy 7.10? Because I would like this stuff to be a bit more straightforward. I am still using 7.04 and have just completed some updates, which included the kernel, and now the latest kernel will not give network connection. I have to boot with the older kernel to get a network, at least that is what is working for me now.

What is the latest information please?
tia

---

### Post by netztier on 2008-01-19
> **candtalan said:**
> What is the latest information please?
tia

It's there.

```
marc@cube:/$ uname -a
Linux cube 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
...
marc@cube:/$ ls -al [COLOR="Red"]/lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000[/COLOR]
total 164
drwxr-xr-x  2 root root   4096 2007-12-20 21:20 .
drwxr-xr-x 23 root root   8192 2007-12-20 21:20 ..
[COLOR="Red"]-rw-r--r--  1 root root 149952 2007-12-18 11:39 **e1000.ko**[/COLOR]
marc@cube:/$ 
```

regards

Marc

---

