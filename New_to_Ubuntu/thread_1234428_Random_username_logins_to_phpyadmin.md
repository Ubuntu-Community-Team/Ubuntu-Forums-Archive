---
title: "Random username logins to phpyadmin"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by tododo on 2009-08-07
Hi all

ive installed phpmyadmin on ubuntu 8.04 and I can reach the php page ok with any username and no password entered.

In fact I cant reach the page when putting the password in...wierd

Dont know where to start

Anybody have any clue
Thanks

---

### Post by Bölvaður on 2009-08-07
look for a hidden folder in your home directory, there might be a config file.

you can also check in synapic which files are created for phpmyadmin, and see if there is one that might help you.


I have no idea.. really Im just bumping your post

---

### Post by tododo on 2009-08-08
Im not 100% sure but I think it may have something to do with the mysql password not being set (although Im sure ive set it in the past)

Anyway ok ive tried resetting that but that is giveing me a world of grief now too

This is where im at now

```
griffithsl@griffithsl-desktop:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                 [ OK ]
griffithsl@griffithsl-desktop:~$ sudo mysqld_safe -skip-grant-tables
nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[6681]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[6687]: ended
griffithsl@griffithsl-desktop:~$ mysql -u root mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

Ive tried a few other things but no joy yet

---

### Post by unutbu on 2009-08-08
If the problem is a missing mysql root password, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1020139&page=2](http://ubuntuforums.org/showthread.php?t=1020139&page=2)

Skip to the end. The easiest way to reset the root password seems to be purging mysql-server-5.0 and mysql-common and then reinstalling. In the process of reinstalling you'll be asked for mysql's root password.

---

### Post by tododo on 2009-08-08
You are the man!!

Cheers dude that fixed it can now logiin as root into phpmyadmin.
Still able to login using any username and no password at all...but with no priveleges in phpmyadmin.......but the main prob is sorted 

Thanks

---

