---
title: "My MYSQL Server not starting..."
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-10-20
Hi

I had problems with my EXT Root filesystem. I corrected it using FSCK. But after that my MYSQL Server is not starting...

> > /etc/init.d/mysql start
 * Starting MySQL database server mysqld   ...fail!

Can anyone please help me fixing this?

---

### Post by Peter09 on 2009-10-20
Try looking in the log files to see if you can find more information.

---

### Post by Guruprasad on 2009-10-20
Thanks for the reply...
Where can I find the mysql log file on my Ubuntu?

---

### Post by Guruprasad on 2009-10-20
ON my system log I found this

> Oct 20 12:10:37 habitatserver /etc/init.d/mysql[14594]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 20 12:10:37 habitatserver /etc/init.d/mysql[14594]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 20 12:10:37 habitatserver /etc/init.d/mysql[14594]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 20 12:10:37 habitatserver /etc/init.d/mysql[14594]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 20 12:10:37 habitatserver /etc/init.d/mysql[14594]: 
Oct 20 12:10:51 habitatserver /etc/init.d/mysql[14746]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 20 12:10:51 habitatserver /etc/init.d/mysql[14746]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 20 12:10:51 habitatserver /etc/init.d/mysql[14746]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 20 12:10:51 habitatserver /etc/init.d/mysql[14746]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 20 12:10:51 habitatserver /etc/init.d/mysql[14746]: 

Is this usefull?

---

### Post by Guruprasad on 2009-10-20
I foound this also in system log

> Oct 20 12:49:47 habitatserver mysqld_safe[14982]: started
Oct 20 12:49:47 habitatserver mysqld[14985]: 091020 12:49:47  InnoDB: Operating system error number 13 in a file operation.
Oct 20 12:49:47 habitatserver mysqld[14985]: InnoDB: The error means mysqld does not have the access rights to
Oct 20 12:49:47 habitatserver mysqld[14985]: InnoDB: the directory.
Oct 20 12:49:47 habitatserver mysqld[14985]: InnoDB: File name ./ibdata1
Oct 20 12:49:47 habitatserver mysqld[14985]: InnoDB: File operation call: 'create'.
Oct 20 12:49:47 habitatserver mysqld[14985]: InnoDB: Cannot continue operation.
Oct 20 12:49:47 habitatserver mysqld_safe[14992]: ended


---

### Post by Peter09 on 2009-10-20
Looks like you have a problem with the file system. Check the directory ./ibdata1

---

### Post by Guruprasad on 2009-10-20
The owner and group of the directory MYSQL was root:root which I changed to mysql:mysql so the access right error was cleared..

But now it is giving someother error

> Oct 20 17:05:29 habitatserver mysqld_safe[6248]: started
Oct 20 17:05:29 habitatserver mysqld[6251]: 091020 17:05:29  InnoDB: Started; log sequence number 0 43655
Oct 20 17:05:29 habitatserver mysqld[6251]: 091020 17:05:29 [ERROR] Fatal error: Can't open and lock privilege tables: File './mysql/host.MYD' not found (Errcode: 2)
Oct 20 17:05:29 habitatserver mysqld_safe[6263]: ended


I check in /var/lib/mysql/mysql directory the file host.MYD is actually missing. How do I get it back?

---

### Post by Wim Sturkenboom on 2009-10-20
Put it back from a backup.

---

### Post by ukripper on 2009-10-20
> **Guruprasad said:**
> The owner and group of the directory MYSQL was root:root which I changed to mysql:mysql so the access right error was cleared..

But now it is giving someother error



I check in /var/lib/mysql/mysql directory the file host.MYD is actually missing. How do I get it back?

where is your mysql backup?Restore from there!

---

### Post by Guruprasad on 2009-10-21
I replaced all the files in /var/lib/mysql/mysql with the new files from the source code I downloaded from MYSQL website. And everything started working. I think few of the files from /var/lib/mysql/mysql were missing due to EXT3 filesystem error.

---

