---
title: "Making MySQL work with PHP"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by jose187 on 2009-04-05
Hi,

Just installed 

Apache 2
MySQL
PHP5, and 
PHPAdmin

I have written a very basic php, and it went well. 

But when i look at the php settings, MySQL in nowhere to be seen. I tried to test MySQL, and it comes back with an error on line 9, which is
```
mysql_connect($host,$user,$password);
```

The question is, how can i connect MySQL to php?
Do i need to create a folder somewhere?
please let me know

---

### Post by scragar on 2009-04-05
Are you sure you installed the php-mysql module:
```
sudo apt-get install php5-mysql
```
Then restart apache:
```
sudo /usr/sbin/apache2cti restart
```

---

### Post by jose187 on 2009-04-05
> **scragar said:**
> Are you sure you installed the php-mysql module:
```
sudo apt-get install php5-mysql
```
Then restart apache:
```
sudo /usr/sbin/apache2cti restart
```

Yes I have, 
I did some further reading and i managed to enable it by editing the php.ini file and pointing it to the right direction of where the mysql.so file was in my computer. So now, that line in the php.ini file looks a bit like this

```
extension_dir= "/usr/lib/php5/some/place"
```

I then restarted apache, and looked at my php settings. MySQL was there...so that did it.

BUT, when i try to test MySQL, it now says 

> 
Warning: mysql_connect() [function.mysql-connect]: Unknown MySQL server host 'hostname' (1) in /var/www/mysql_up.php on line 9

Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/mysql_up.php on line 11

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/mysql_up.php on line 11
Error 1045: Access denied for user 'www-data'@'localhost' (using password: NO)

I am asuming i need to give it the user name, password, etc...
how do i do it?

---

### Post by freak42 on 2009-04-05
```
and it comes back with an error 
```

the 'an error' is quite a bad error.. no one was ever able to resolve this one.

;-)

---

### Post by scragar on 2009-04-05
> **jose187 said:**
> Yes I have, 
I did some further reading and i managed to enable it by editing the php.ini file and pointing it to the right direction of where the mysql.so file was in my computer. So now, that line in the php.ini file looks a bit like this

```
extension_dir= "/usr/lib/php5/some/place"
```

I then restarted apache, and looked at my php settings. MySQL was there...so that did it.

BUT, when i try to test MySQL, it now says 



I am asuming i need to give it the user name, password, etc...
how do i do it?

Mysql_Connect takes three arguments, a host(probably 'localhost') a username(unless you've used mysql-admin to add another user, probably 'root') and a password(you should know this :p)

---

### Post by jose187 on 2009-04-05
> **scragar said:**
> Mysql_Connect takes three arguments, a host(probably 'localhost') a username(unless you've used mysql-admin to add another user, probably 'root') and a password(you should know this :p)

Thanks, but how do i check or change the user name. Root doesn't seem to work.

EDIT: Never mind- It does work with root and my password. I had the host as my computer's name, should have been "localhost" as you so rightly said.

Another problem solved by the mighty forum. 
Plenty of Win in this place.
Thank you scragar for your help.

---

### Post by scragar on 2009-04-05
> **jose187 said:**
> Thanks, but how do i check or change the user name. Root doesn't seem to work.

EDIT: Never mind- It does work with root and my password. I had the host as my computer's name, should have been "localhost" as you so rightly said.

Another problem solved by the mighty forum. 
Plenty of Win in this place.
Thank you all very much for your help.

'root' is the default admin username, it cannot be changed as far as I know. Use mysql-admin and add another user.

---

