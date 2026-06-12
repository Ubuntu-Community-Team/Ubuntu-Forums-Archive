---
title: "MySql denies me access!"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by Category on 2007-04-16
No matter which user I use (including root via sudo), my LAMP server refuses to let me access MySql server, whether I'm on the local machine or not. Please help me!

I'm trying to set up phpBB on my web server, but without access to MySql, I am quite stuck. Here is what it outputs on the shell:

> category@linuxbox:~$ sudo mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


All help is appreciated - it's driving me crazy!

---

### Post by zvezdogled on 2007-04-16
when setting up mysql server, did u set the database administrators password?
What i ment is. When installing mysql server you have to set the root password, wher root is not the system root but the database admin. This is done via 

mysqladmin -u root password 'thepassword'

and then you connect to mysql:

mysql -u root -p
and when asked for password type 'thepassword'

you can read more on 
[http://www.linuxforums.org/servers/setting_up_a_server.html](http://www.linuxforums.org/servers/setting_up_a_server.html)

---

### Post by Category on 2007-04-16
> category@linuxbox:~$ sudo mysqladmin -u root password 'thepassword'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I didn't set an admin password before, and that is what happens when I try to set one. MySql was installed as part of the "Install LAMP Server" option, if that has any effect.

[EDIT] I uninstalled, reinstalled, and still get the same error. If anybody can help, please do!

---

### Post by VorDesigns on 2007-05-17
I just built a server and I though I told the system it was supposed to be a LAMP server:
Linux HashiNoHashiNi 2.6.17-10-server #2 SMP Tue Dec 5 22:29:32 UTC 2006 i686 GNU/Linux
- 
When I tried to access the web site, nada.
-
Plodding through the server guide, I installed patches, Apache2, sshd and now MySQL.
I followed the process

> By default, the administrator password is not set. Once you install MySQL, the first
thing you must do is to configure the MySQL administrator password. To do this, run the
following commands:
sudo mysqladmin -u root password newrootsqlpassword

Returned to the prompt without issue.

I then entered the next instructed command

> sudo mysqladmin -u root -h localhost password newrootsqlpassword

```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

But, 

> mysql -u root -p

Works like a charm.

Is the issue that I'm not doing this at the console or is this even necessary.

I would like to fix this before I move on.

---

### Post by Rojahon on 2007-07-12
For future reference if anyone has this problem, this is what I did:

(From: [http://www.debianadmin.com/recover-mysql-database-root-password.html](http://www.debianadmin.com/recover-mysql-database-root-password.html))

> Stop the MySQL server by using either of the following command

#/etc/init.d/mysql stop

Now you need to Start MySQL server without password

# mysqld_safe --skip-grant-tables &

Connect to mysql server using mysql client with the following command

# mysql -u root

Now you should be having mysql prompt

mysql>

Now you need to Setup new MySQL root user password

mysql> use mysql;

mysql> update user set password=PASSWORD(”newrootpassword”) where user=’root’;

mysql> flush privileges;

mysql> quit

Note: Replace newrootpassword with the new root password for MySQL server. Flush Privileges is needed to making the password change effect immediately.

Now you need to Stop MySQL Server using the following command

# /etc/init.d/mysql stop

Test Your New Mysql root password

First you need to start mysql server using the following command

# /etc/init.d/mysql start

# mysql -u root -p

Now it will prompt for root password and enter your new root password

---

### Post by Ibane on 2007-07-18
Hello all,
I am having the same problem described here but I can not even has access. 

If I try to set the new password I cannot either.

# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Thanks,

---

### Post by az on 2007-07-18
> **Ibane said:**
> Hello all,
I am having the same problem described here but I can not even has access. 

If I try to set the new password I cannot either.

# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Thanks,

Your password was already set, that's why it is compaining.  Do the steps detailed in the above post to reset your mysql password.

---

### Post by Ibane on 2007-07-19
Thanks,

The issue was that I was not able to stop the process mysqld_safe. After I stopped it then I followed the instructions and everything worked fine.

---

