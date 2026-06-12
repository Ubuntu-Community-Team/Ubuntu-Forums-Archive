---
title: "Argh- resolving aborted package installation (mysql)"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by submute on 2010-07-02
I tried to 'aptitude install mysql-server' and it just hung on the configuration of my.cnf. I had to kill the process. Then I tried aptitude remove of the same package, and it hung.

What's the best way to resolve this so it's a clean install of the MySQL package?

Thanks!

The result of dpkg -i | grep mysql yields the following. The 'rF' kinda scares me. What's it mean?


ii  mysql-client-5.1                5.1.41-3ubuntu12.3                MySQL database client binaries
ii  mysql-client-core-5.1           5.1.41-3ubuntu12.3                MySQL database core client binaries
ii  mysql-common                    5.1.41-3ubuntu12.3                MySQL database common files (e.g. /etc/mysql
rF  mysql-server-5.1                5.1.41-3ubuntu12.3                MySQL database server binaries
ii  mysql-server-core-5.1           5.1.41-3ubuntu12.3                MySQL database core server files

Also, when I try to aptitude remove mysql-server, it just gets here...


The following packages will be REMOVED:
  mysql-server-5.1{u} 
0 packages upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 15.0MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 77521 files and directories currently installed.)
Removing mysql-server-5.1 ...

And then hangs until I kill it. Help! :)

---

### Post by gzarkadas on 2010-07-03
Try to first stop the mysql daemon:
```

sudo /etc/init.d/mysql stop

```Then instruct aptitude to remove *everything* from mysql-server:
```

sudo aptitude purge mysql-server

```

---

