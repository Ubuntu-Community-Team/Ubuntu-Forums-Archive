---
title: "Hardy Heron: MySQL installation problems"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Gakumerasara on 2009-01-17
I'm a Linux newbie trying to get mysql up and running.
following the instructions here: [http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html](http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html)

installed mysql-5.0
```
sudo apt-get install mysql-server
```
```
sudo /usr/bin/mysql_install_db --user=XXX
```

error "[Warning] Ignoring the user change to 'XXX' because the user was set to 'mysql' earlier on the command line." pops up twice in the resulting text.  Other than that, it seemed to work okay.

then: ```
sudo /usr/bin/mysqladmin -u XXX password XXX
```
or: ```
sudo /usr/bin/mysqladmin -u XXX -password XXX
```

error: 'Access denied for user 'XXX'@'localhost' (using password: YES)'

What am I doing wrong, here?  :confused:

I uninstalled it using Synaptic and reinstalled it only to get the same result.

---

### Post by Cypher on 2009-01-17
Hmm..I've always just done the "apt-get" command you've done above, and then logged into MySQL as root with
```

mysql -uroot

```
Once logged in as root, you then use something like
```

GRANT ALL PRIVILEGES ON *.* TO '<user>@localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;
FLUSH PRIVILEGES;

```
This creates my user account which I use for all further actions with MySQL. You fill out the <user> and <password> parts..

---

