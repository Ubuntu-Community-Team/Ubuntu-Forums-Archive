---
title: "I want to learn PHP, how can I preview on my computer?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by jose187 on 2009-03-24
Hi,

I am using Ubuntu 8.1.

I want to learn PHP, but i want to be able to preview it on the browser without having to ftp it to another server...so it's local stuff.

I have looked at other threads, and I have been able to install Apache2, php5, and MySql, then restarted apache. I got the /var/www folder with the html index and all.

I created a simple PHP file with the typical "Hello Word", but every time i open in on a web browser, it keeps asking me if i want to download it.

What am i doing wrong?

Can somebody please help.

Thanks

---

### Post by mvalviar on 2009-03-24
Xampp! Get it here > [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

---

### Post by WorldTripping on 2009-03-24
This is from the Ubuntu help page.

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

> **Troubleshooting PHP 5**
Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. 

You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it. 

Be sure to clear your browser's cache before testing your site again. 


---

### Post by WorldTripping on 2009-03-24
If you are looking at php you might want to install phpMyAdmin too.

Cheers.

---

### Post by mcduck on 2009-03-24
> **jose187 said:**
> Hi,

I am using Ubuntu 8.1.

I want to learn PHP, but i want to be able to preview it on the browser without having to ftp it to another server...so it's local stuff.

I have looked at other threads, and I have been able to install Apache2, php5, and MySql, then restarted apache. I got the /var/www folder with the html index and all.

I created a simple PHP file with the typical "Hello Word", but every time i open in on a web browser, it keeps asking me if i want to download it.

What am i doing wrong?

Can somebody please help.

Thanks
Even with Apache and PHP installed you won't be able to open the PHP file itself in the browser. It's not a web page, it's a script the server runs to generate the web page viewable in browsers. So you need to run it through the server.

Put the .php file into /var/www and then in your browser use "localhost" as address to open your web page.

---

### Post by jose187 on 2009-03-24
Thank you all for the help.

I was being a bit of an idiot, and didn't place the files where they should have been.

As I said before, I installed PHP, Apache2, and MySQL as explained in this website

[http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/](http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/)

It says its for Ubuntu 8.04, but it was fine for 8.10 too (I Hope, don't quote me on that).

The reason why it wasn't showing up was because the PHP file i had made was on the desktop *slaps forehead*, whereas it should have been in the following folder

/var/www

Once it was transfered there, i opened it on the web browser using this address:

[http://localhost/hello.php](http://localhost/hello.php)

the name of the file i made being "hello.php"

That got rid of all the download messages, and displayed the page properly.

Sorry for wasting people's time, but that you all for your help.

---------------------
edit:

Beat me to it mcduck. That was spot on, thanks!

---

### Post by WorldTripping on 2009-03-24
For future reference you might have to

> chown -R /var/www user:user
and
> chmod -R 755 /var/www

To prevent any permission errors.

Cheers.

---

### Post by WorldTripping on 2009-03-24
> **jose187 said:**
> Thank you all for the help.

I was being a bit of an idiot, and didn't place the files where they should have been.

As I said before, I installed PHP, Apache2, and MySQL as explained in this website

[http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/](http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/)

It says its for Ubuntu 8.04, but it was fine for 8.10 too (I Hope, don't quote me on that).

The reason why it wasn't showing up was because the PHP file i had made was on the desktop *slaps forehead*, whereas it should have been in the following folder

/var/www

Once it was transfered there, i opened it on the web browser using this address:

[http://localhost/hello.php](http://localhost/hello.php)

the name of the file i made being "hello.php"

That got rid of all the download messages, and displayed the page properly.

Sorry for wasting people's time, but that you all for your help.

---------------------
edit:

Beat me to it mcduck. That was spot on, thanks!


oops..my fault..should have asked the simplest of questions first.."Is the .php file in the right place ?"

---

### Post by jose187 on 2009-03-24
> **WorldTripping said:**
> oops..my fault..should have asked the simplest of questions first.."Is the .php file in the right place ?"

it's in 

/var/www

and i have just changed the permission too, to 755. Thanks for the tip.

---

