---
title: "MySQL on Ubuntu but data files on Windows Share"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Jeinhor on 2007-09-06
Hello, 

I have a windows share mounted at /mnt/mysql on my machine (Ubuntu 6.06, MySQL 5.0). I would like to use this location as a storage for my data files for mysql. 

I've mounted the Windows Share using Samba and with the filesystem "cifs". I've changed the datadir-value in /etc/mysql/my.cnf to /mnt/mysql. 

But when I run (as root) mysqld it says: 
InnoDB: operating system error number 13 in a file operation 
InnoDB: The error means mysqld does not have the access rights to 
InnoDB: the directory. 
InnoDB: File name ./ibdata1 
InnoDB: File operation call: 'open' 
InnoDB: Cannot continue operation. 

777 has permission to /mnt/mysql. Also, I've looked at /var/lib/mysql to check which ownership the different files should have and changed my datadir to look the same, but with no luck. 

The data files have been used on a Windows MySQL Server before, and now I'm trying to run the MySQL-server on Linux instead, but keeping the datafiles in Windows. 

Why can't I start mysqld? 

(I posted this at mysql.com, but since there was no replies I figured it might be a OS-dependent problem?)

Thanks in advance!

---

