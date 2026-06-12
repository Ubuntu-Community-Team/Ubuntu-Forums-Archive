---
title: "Cannot install MySql server"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by weiyan on 2011-08-02
In the software centre, install MySQL database server(metapackage depending on the latest version), never success. 

When install, a prompt appear:

 If install MySQL server, following must be removed:
```
Mysql database client binaries
mysql-cluster-client-5.1
Mysql database server binaries
mysql-cluster-client-5.1

```clicked install, running for a while, if ptompts "Repository installation failed". 

Then prompt for repair.

In the /usr/bin, found mysql* files and mysql process in system monitor.

Tried install mariadb, the same problem exists.

It seems the first installation failed in half way, leave something there. Is any means to repair?

Thanks.

---

### Post by Chiel92 on 2011-09-28
Maybe you could install mysql another way?
E.g. [http://ariejan.net/2007/12/12/how-to-install-mysql-on-ubuntudebian](http://ariejan.net/2007/12/12/how-to-install-mysql-on-ubuntudebian)

If you also need php or apache, I recommend to install a complete LAMP server by following an how-to:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

