---
title: "[Tutorial] How to install Apache for linux [/Tutorial]"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Èync on 2007-07-24
First we install Apache, PHP and mySQL. Open your terminal and type:
```
sudo apt-get install apache2 php4 libapache2-mod-auth-mysql php4-mysql mysql-server
```

After that we setup for mySQL password
```
mysqladmin -u root password Here_your_password
```

Now you have Apache, PHP and mySQL. Put ur sites now to /var/www/ file

---End----- Now you have working apache web server :D

**Do you want see the sites ONLY for your computer**
Write in terminal
```
sudo gedit /etc/apache2/ports.conf
``` 

**GD support**
Write in terminal
```
sudo apt-get install php4-gd
```

**PHPMyadmin**
Write in terminal
```
sudo apt-get install phpmyadmin
```
your phpmyadmin's link: [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Restart after these updates Apache and mySQL 
```
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart
```

**IF** Apache or mySQL aren't running 
```
sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysql start
```



_--Please Leave comments....

---

### Post by Èync on 2007-07-25
Bump have been 2 days

---

### Post by Èync on 2007-08-04
bump have been over week

---

### Post by CyDharttha on 2007-09-27
php4 packages are no longer available afaik, using php5 and php5-mysql works just great! Thanks for the guide Eync!

---

