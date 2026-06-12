---
title: "Reinstall LAMP"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Dbugger on 2009-01-02
Hi guys. I've tried to set up a LAMP system but I messed up too bad that I want to start from square 1.

How can I remove a LAMP system completely? That means no configfile, no temp files, no nothing!

Please help me! Thank you!

---

### Post by blueridgedog on 2009-01-02
You may try ```
apt-get clean
``` or a clean install of server if you think it is that bad.

---

### Post by northern lights on 2009-01-02
Open a Terminal (Applications > Accessories > Terminal) and run```
sudo aptitude purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```to remove the entire LAMP stack.

P.S. Shift+Ctrl+V pastes into terminal...

---

