---
title: "SSL not Working in Ubuntu 9.10"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by subodh.rohilla on 2010-03-11
I am trying to add ssl support for apache in ubuntu 9.10. I gave the following commands : 

1) a2enmod ssl
2) /etc/init.d/apache2 restart

First command shows that it is already enabled but when i run command : 

netstat -tap | grep https

It gives no entry for apache2 i.e. apache is not listening https . I am not able to figure out where the error is ??????

---

### Post by sandyd on 2010-03-11
you need to set a ssl cerficiate and key in the apache2 configuration before ssl will work.

---

