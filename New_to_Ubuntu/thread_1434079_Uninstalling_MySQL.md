---
title: "Uninstalling MySQL"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-03-19
Hey, I followed this guide ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)) to uninstall all the packages from my computer. Are all the data in the MySQL database still stored on my computer? Would it be safe for me to just delete them (they're in /var/lib/, right)?

---

### Post by wjm on 2010-03-19
Did you pull it out correctly this way:

sudo aptitude --purge remove mysql-server

---

### Post by mathfreak123 on 2010-03-19
I used sudo apt-get get remove/autoremove. Would that work as well?

---

