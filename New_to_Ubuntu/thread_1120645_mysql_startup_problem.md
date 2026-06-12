---
title: "mysql startup problem"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by timmè on 2009-04-09
hi lads,
i installed apache + mysql + php two days ago, but mysql did not started, so i manually downloaded and installed it, then it worked. But after reboot mysql failed to startup again.
the error was that there was another sql already running.
please help me! im a new with linux.
my terminal output:
----------------------------------------------------------------------------
tim@tim-laptop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP for Linux started.
tim@tim-laptop:~$ sudo /etc/init.d/mysqld stop
sudo: /etc/init.d/mysqld: command not found
tim@tim-laptop:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                 [ OK ] 
tim@tim-laptop:~$ sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.5.3a...
XAMPP: Stopping Apache with SSL...
XAMPP: XAMPP-MySQL is not running.
XAMPP stopped.
tim@tim-laptop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP for Linux started.
tim@tim-laptop:~$ /opt/lampp/bin/mysql.server: 334: log_failure_msg: not found
---------------------------------------------------------------------------

thanks

---

### Post by jaytek13 on 2009-04-09
How did you determine that MySQL failed to start? 

I see in your commands you successfully stopped it by using /etc/init.d/mysql stop... have you tried /etc/init.d/mysql start? 

If you installed it from source that would be the normal thing to do. I am not familiar with xampp, but it does sound like you have 2 installations now. If that's a package, then personally, I'd start over and install Apache, PHP, and MySQL by themselves.

---

### Post by timmè on 2009-04-09
i just uninstalled and then reinstalled mysql-server.
but when i use:"/etc/init.d/mysql start"
i got a permission denied error.
what should i do next to get permission to start?
thanks

---

### Post by timmè on 2009-04-09
ok, i give up...:(
nothing seems to work.
im going for a complete reinstall of apache and mysql

---

### Post by timmè on 2009-04-09
no, ill never give up!! :)
------------------------------------------
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP: Starting MySQL...
XAMPP for Linux started.
---------------------------------------------

please help me ;)
--------------------------------------------
/opt/lampp/bin/mysql.server: 84: source: not found 
--------------------------------------------
wtf is this error??

should i bind to another socket?
is it a permission problem?
...?

---

### Post by unutbu on 2009-04-09
Maybe there is a way to use xampp with Ubuntu, but I haven't read any happy reports about it here at ubuntuforums. It appears the Ubuntu way of setting up mysql,php and apache is to uninstall xammp
and then run
```

sudo apt-get install mysql-server-5.0 apache2 libapache2-mod-php5
```

---

### Post by timmè on 2009-04-09
thx for replying.
the strange thing is i got it to work once, but after reboot it won't run again.
what is the best way to uninstall lampp and mysql?

---

### Post by unutbu on 2009-04-09
How was xampp installed? Did you run
```

sudo make install
```
? If so, perhaps try 
```

cd /path/to/xampp/source/code
sudo make uninstall
```

---

### Post by timmè on 2009-04-09
thx it now works!!
thank you very, very much!:)
but when i installed phpmyadmin and went to "http://localhost/phpmyadmin"
it asked for a username and password??
where can i find/set these?

---

### Post by unutbu on 2009-04-09
When you installed mysql-server, your were prompted for a mysql root password. (Note this is not related to your Ubuntu root password).

You can log in to phpmyadmin by using "root" as the username and the mysql root password for the password.

---

### Post by timmè on 2009-04-09
i already tried that usrname and passw but it didn't get accepted...because i forgot to start the mysql server. silly me :)
but all is finally working like it should now.
thanks again for helping!

---

