---
title: "mysqld.sock missing"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by beelzebufo on 2011-06-14
I know this has been discussed before, but I cannot find anything that actually helps me for some reason.  I have renamed the mysqld.cnf file, I have followed all kinds of tutorials, but for some reason.. none of them solve the problem.  I keep getting 


neganx@sledgehammer:/usr/bin$ ./mysqladmin ping
./mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
neganx@sledgehammer:/usr/bin$ 

and I have no idea why 

I uninstalled and reinstalled... all kinds of things...
help!!
thanks in advance
beelzebufo

followed [http://linux.about.com/od/nwb_guide/a/gdenwb01t88.htm](http://linux.about.com/od/nwb_guide/a/gdenwb01t88.htm)

and a few others, any help would be awesome

---

### Post by jtarin on 2011-06-14
> **beelzebufo said:**
> 
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
And did you? You don't say so in your post.

---

### Post by beelzebufo on 2011-06-14
oh sorry, in my frustration I didn't include that, the mysql.sock is missing and I cannot, for the life of me find any way to replace it.. I may just not be looking in the right places, but I tried everything from every thread in every forum I could find with a google search for mysqld.sock missing

---

### Post by beelzebufo on 2011-06-15
ok, so.. now I am here.. still totally frustrated any help would be amazing.  How do I not have permission? this makes no sense

got the thing running, I was just missing a step that I hadn't seen and that was the mysql_safe script here is my terminal activity


```
s3ct10n_8@wreckingball:~$ sudo /usr/bin/./mysqld_safe
110614 20:04:18 mysqld_safe Logging to syslog.
110614 20:04:18 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

```

```
s3ct10n_8@wreckingball:~$ sudo nano /etc/mysql/my.cnf
[sudo] password for s3ct10n_8: 
s3ct10n_8@wreckingball:~$ sudo mysqld start
s3ct10n_8@wreckingball:~$ 

```

and the "makes me want to punch kittens" line

```
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ mysqladmin ping
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 's3ct10n_8'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ sudo mysqladmin ping
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ sudo mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ mysqladmin -u root password ""
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ mysqladmin -u root password ''
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ mysqladmin -u root password 'root'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ sudo mysqladmin -u root password 'root'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ sudo mysqladmin -u root password "root"
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
s3ct10n_8@wreckingball:/pentest/exploits/framework3$ 

```

---

