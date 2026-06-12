---
title: "How do I re-instate a mysqld.sock file?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by bwallum on 2010-01-27
Hi

Just when I thought I was getting on top of MySQL I have managed to lose the mysqld.sock file, which I understand is needed to start up mysql.

I had been using a beta version of MySQL Workbench last night. This morning no mysqld.sock file. Probably related but not sure how. Can't find it at all using search of entire filesystem.```
mysqladmin --socket=/tmp/mysqld.sock version
```returned > mysqladmin: connect to server at 'localhost' failed error: 'Can't connect to local MySQL server through socket '/tmp/mysqld.sock' (2)'```
mysql -ubob -hlocalhost -P3306 -p
``` returned> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Can you help me re-instate the mysqld.sock file please?

---

### Post by Stoneface on 2010-07-18
Were you ever able to fix this?

---

### Post by bwallum on 2010-07-19
Hi

No, I never understood what happened and did a re-install of mysql, at which point all ran well again.

---

### Post by alligater on 2010-10-20
i have tried to link a sock file for mysql as follow:

#cd /tmp
#sudo ln -s /var/run/mysqld/mysqld.sock mysqld.sock
#sudo /etc/init.d/mysql start

And mysql is working now

---

### Post by Jense on 2010-10-20
I have the same problem. I tried reinstalling mysql-server, tried to set permissions manually

```

# ls -l /var/run/ | grep mysql
drwxrwxr-x 2 mysql      mysql        60 2010-10-20 12:16 mysqld

# ls -l /var/run/mysqld/mysqld.sock 
-rw-rw-r-- 1 mysql mysql 0 2010-10-20 12:16 /var/run/mysqld/mysqld.sock

```

This problem occurd after I upgrade from 8.04 to 10.04. During the upgrade from 9.10 to 10.4 the system hang for ages on setting up mysql. I hat to Ctrl-C that. Afterwards reinstalling mysql-server (tried ```

apt-get remove mysql-server
apt-get autoremove
apt-get install mysql-server

```)

I also tried to set up the symlink, but that didn't help either.

Any ideas?
I ran into the same problem. Really in a fix here and need this DB, so if you have any more ides? Please help

I opened a new thread here: [http://http://ubuntuforums.org/showthread.php?p=9999987#post9999987]("http://ubuntuforums.org/showthread.php?p=9999987#post9999987")

---

### Post by gsocker on 2010-10-20
This "file" is created my the MySQL server at startup. If it doesn't exist, then either mysqld is not running or the file is somewhere else(the path can be changed on the command line).

Trying to create the file by hand won't work.
It isn't actually a file; it's a unix socket.

Try running ```
netstat -ln | grep mysql
``` and see if you get anything.

On my system, this returns 
```

unix  2      [ ACC ]     STREAM     LISTENING     2397550 /var/run/mysqld/mysqld.sock

```

---

### Post by peragrate72 on 2011-10-15
Hi. I ran that code:

```
netstat -ln | grep mysql
```

Immediately, nothing was returned, yet which shows:

```
/usr/bin/mysql

```

And trying to run:

```
sudo service mysqld status
```

...returns 

```
mysqld: Unrecognized Service.
```

Apt is locked up right now, so I'm going to restart the machine, and see if I can completely remove mysql and compile instead.

Phpmyadmin isn't working because of this problem too, and now I can't uninstall that (because it can't connect to mysql)...

---

