---
title: "Don't want mysql and apache to load on startup"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-13
Web development takes up about 50% of the the time I spend on my laptop. So for the other 50% I don't need apache and mysql. However I've noticed that both these programs automatically load on startup. Is there a way to disable them from loading on startup?

---

### Post by Celauran on 2009-07-13
I just leave them running as they consume next to zero resources when not in active use. Still, if you'd like them disabled, you go uncheck them from System -> Administration -> Services and turn them on only when needed.

---

### Post by carrarin on 2009-07-13
chkconfig

chkconfig -del mysql
"            " apache

?

---

### Post by Neo4 on 2009-10-08
> **Celauran said:**
> I just leave them running as they consume next to zero resources when not in active use. Still, if you'd like them disabled, you go uncheck them from System -> Administration -> Services and turn them on only when needed.
how can I do that on ubuntu 9.10?

I don't have any services under admin

---

### Post by kanikilu on 2009-10-08
```
sudo update-rc.d -f apache2 remove
sudo update-rc.d -f mysql remove
```

---

