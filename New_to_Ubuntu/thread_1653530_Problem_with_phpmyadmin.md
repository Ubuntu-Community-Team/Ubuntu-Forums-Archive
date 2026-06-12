---
title: "Problem with phpmyadmin"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by ballacksam on 2010-12-27
Hello All,

I installed lamp package through these commands
Apache:
sudo apt-get install apache2[FONT=monospace]

PHP:
[/FONT]sudo apt-get install php5 libapache2-mod-php5[FONT=monospace]
[/FONT]sudo /etc/init.d/apache2 restart[FONT=monospace]

[/FONT]MYSQL:
sudo apt-get install mysql-server[FONT=monospace]
[/FONT]sudo apt-get install mysql-admin[FONT=monospace]
[/FONT]killall gnome-panel
[FONT=monospace]
[/FONT]sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

To get PHP to work with MySQL
gksudo gedit /etc/php5/apache2/php.ini

uncomment :extension=mysql.so

Restart apache
sudo /etc/init.d/apache2 restart



All things work: the server when testing [http://localhost](http://localhost)
and php when testing [http://localhost/info.php](http://localhost/info.php)

But the problem is in phpmyadmin when login from 
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)  it go to a login page then I typed the username 
and password I set and when submitted an error message display:
**#2002 Cannot log in to the MySQL server**

I installed myql again and when login this error display:
[B]phpMyAdmin - Error
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.[/B] 

What can I do to solve this ?

Thanks in advance

---

### Post by smuthavarapu on 2010-12-27
This might help you [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

