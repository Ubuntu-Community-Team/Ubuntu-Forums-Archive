---
title: "Help with XAMPP MySQL"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by jasperleeabc on 2010-05-13
Hi,

I need some help with XAMPP (version 1.7.3a). My MySQL cannot be started, while the Apache and ProFTPD can be started smoothly. When I start it it's like:

```

Starting XAMPP for Linux 1.7.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

```So I looked into the MySQL log and found this:

```

100513 14:53:22 mysqld_safe Starting mysqld daemon with databases from /opt/lampp/var/mysql
100513 14:53:22 [Note] Plugin 'FEDERATED' is disabled.
100513 14:53:22 [ERROR] Can't open shared library 'libpbxt.so' (errno: 0 API version for STORAGE ENGINE plugin is too different)
100513 14:53:22 [Warning] Couldn't load plugin named 'PBXT' with soname 'libpbxt.so'.
100513 14:53:22  InnoDB: Started; log sequence number 0 44233
100513 14:53:22 [ERROR] Can't start server : Bind on unix socket: Permission denied
100513 14:53:22 [ERROR] Do you already have another mysqld server running on socket: /opt/lampp/var/mysql/mysql.sock ?
100513 14:53:22 [ERROR] Aborting

100513 14:53:22  InnoDB: Starting shutdown...
100513 14:53:24  InnoDB: Shutdown completed; log sequence number 0 44233
100513 14:53:24 [Note] /opt/lampp/sbin/mysqld: Shutdown complete

100513 14:53:24 mysqld_safe mysqld from pid file /opt/lampp/var/mysql/jasperleeabc-desktop.pid ended

```Any idea how to solve this?

Thanks.

---

### Post by jasperleeabc on 2010-05-15
bump. Sorry but I really haven't got any reply. Really need this solved...

---

