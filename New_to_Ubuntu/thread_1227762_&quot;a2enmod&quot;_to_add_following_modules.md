---
title: "&quot;a2enmod&quot; to add following modules"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by 007casper on 2009-07-31
How do I use "a2enmod" to add following modules

proxy_ajp.load -> ../mods-available/proxy_ajp.load
proxy.conf -> ../mods-available/proxy.conf
proxy_http.load -> ../mods-available/proxy_http.load
proxy.load -> ..../mods-available/proxy.load

I tried 
sudo a2enmod proxy_ajp.load -> ../mods-available/proxy_ajp.load

it states permission denied ???

---

### Post by credobyte on 2009-07-31
```
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod proxy_ajp

```

---

### Post by 007casper on 2009-07-31
thank you so much!!! cheers

---

