---
title: "Apache/PHP configuration problem"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Hobbes20xx on 2009-12-12
Hey all, so first off i would like to say im new(obviously) but pretty decent in general with computers, so step by step would be nice, but not necessary.

Anyways, im attempting to setup a home web server using ubuntu  v8.01, and following the guidelines that can be seen [here]("http://net.tutsplus.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/"). The problem im having is when i go to configure apache to disclose the minimum amount of info necessairy, i cannot find the "ServerSignature On" line after copying the file and opening it with these commands : 
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
then
sudo nano /etc/apache2/apache2.conf

any help would be appreciated, thanks ahead of time. :D

---

### Post by bodhi.zazen on 2009-12-12
Search fo rit with grep ;)

```
grep -R ServerSig /etc/apache2
```On my system it was in /etc/apache2/conf.d/security

---

### Post by Hobbes20xx on 2009-12-13
Thanks alot, problem solved.

---

