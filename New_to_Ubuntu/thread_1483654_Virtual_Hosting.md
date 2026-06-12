---
title: "Virtual Hosting"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by macmike on 2010-05-14
I have followed the Debian-Adminstration guide number 412 trying to set up Virtual Hosting for three sites. I now get the following errors.

NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

Any help appreciated.

---

### Post by slibuntu on 2010-05-14
That's just a warning, Apache should start up ok. Are pages being served correctly? The problem is something wrong with your apache conf

This page may help. [http://www.mydigitallife.info/2007/08/11/apache-warn-namevirtualhost-80-has-no-virtualhosts-error-when-start/](http://www.mydigitallife.info/2007/08/11/apache-warn-namevirtualhost-80-has-no-virtualhosts-error-when-start/)

---

