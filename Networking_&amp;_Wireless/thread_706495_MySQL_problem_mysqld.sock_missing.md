---
title: "MySQL problem mysqld.sock missing"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by pichon on 2008-02-24
I can't run MySQL server when I try to see the version I get this message:

```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

If I list the files in /var/run/mysqld/ I have nothing.  I read in this forum that by just adding the file It should work, what does the file have to contain?

Thanks in advance everyone!!!

PME

---

