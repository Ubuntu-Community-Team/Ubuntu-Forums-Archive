---
title: "apache + phpmyadmin 404/403 after update to 15.04"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by aftershave-and-co on 2015-08-05
Hello,

Yesterday, when i was on 14.10, i was using a folder in my home to install my website in developpment. And i used phpmyadmin to manage my database.
To achieved that i modified DocumentRoot /home/USER/Localhost in  /etc/apache2/sites-available/000-default.conf.

Since i update to 15.04, i get errors 404 or 403.
I did the update through ubuntu, it's not a fresh install. As i remember, the installation finished without any problem at first sight.
I can't remember when i updated ubuntu without problem with apache configuration.:popcorn:

Today, apache and mysql seem to work. I get ok when i restart apache with:
```
sudo /etc/init.d/apache2 restart
```
But as i got some error 404, i tried to reinstall apache without any succes:

```
sudo apt-get --purge remove apache2 
```
```

sudo apt-get install apache2 
sudo apt-get install php5 php5-mysql php5-mcrypt php5-gd libapache2-mod-php5
```

When i try to reset phpmyadmin it doesn't work and i get an error
```
sudo dpkg-reconfigure -plow phpmyadmin

``````
Job for apache2.service failed. See "systemctl status apache2.service" and "journalctl -xe" for details.
invoke-rc.d: initscript apache2, action "reload" failed.
Job for apache2.service failed. See "systemctl status apache2.service" and "journalctl -xe" for details.
invoke-rc.d: initscript apache2, action "reload" failed.

```


**First issue** why i get different answer error with localhost:
when i try [http://localhost/index.html](http://localhost/index.html) > i get apache's default page > ok
when i try [http://localhost/test.html](http://localhost/test.html) dans /var/www/html donc  > i get my test page > ok
when i try [http://localhost/phpinfo.php](http://localhost/phpinfo.php) dans /var/www/html donc  > error 403 > ko
when i try [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  > error 404 > ko


About the 403 error, i suspect a right problem but the php seems t have the same permission than the html file:

```
-rw-r--r-- 1 root root 11510 avril 26  2014 index.html
-rw-r--r-- 1 root root  3356 août   2 22:33 index.lighttpd.html
-rw-r--r-- 1 root root    20 août   3 22:33 phpinfo.php
-rw-r--r-- 1 root root 11517 août   4 06:38 test.html

```

**Second issue**, to use my folder in home as i did 
when i modify DocumentRoot /home/USER/Localhost in  /etc/apache2/sites-available/000-default.conf  add i try again [http://localhost/phpinfo.php](http://localhost/phpinfo.php) in /home/USER/Localhost donc  > error 404 > ko


In **/var/log/apache2**
[I]Log are empty
[/I]

I tried to configure it in **/etc/php5/apache2/php.ini**, without any new informations:

```
error_reporting = E_ALL | E_STRICT
error_log = /var/log/apache2/php_errors.log

```

In **/var/log/mysql**

```
150804 23:55:40 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
150805 00:05:40 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
/usr/sbin/mysqld: Can't read dir of '/etc/mysql/mysql.conf.d/' (Errcode: 13 - Permission denied)
Fatal error in defaults handling. Program aborted

```


For information, i opened the ort 80 throught Gufw.
And i add my user to www-data group:

```
www-data:x:33:USER

```

How solve the issue to use apache as i did?
Could it be an issue with my php install?
Why apache do differently with .html and .php?

Secondly we will try to make mysql and phpmyadmin work


Any help will be appreciate.

Thank you in advance,
jb

---

