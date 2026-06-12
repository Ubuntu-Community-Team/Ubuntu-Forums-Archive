---
title: "Newbies guide to install LAMP on Ubuntu"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by s.a.patil on 2011-05-03
Newbies guide to install LAMP on Ubuntu

Cover Ubuntu 10.4.2 LTS, can also be applied to lower or higher version of Ubuntu

The guide is intended to help those who have very little knowledge of using Ubuntu Linux, any improvement would be really appreciated.

If you're developing websites based on popular language PHP, it's nice to be able to test your code in the privacy of your own computer rather that out in the public internet. In order to do that, you'll need to install a web-server on your development computer. LAMP (Stands for L=Linux, A=Apache, M=MySQL, P=PHP) is one of the most common web hosting platforms, so it's a perfect environment for you to build and test your website code. If you carefully follow these step by step instructions thoroughly, you'll have your own LAMP server setup running in no time.

Step No: 1
Ubuntu developers have made it easy to install the LAMP server packages with a single command. 

1. Simply Open up the Terminal (Applications > Accessories > Terminal).

2. Type the following line of code into Terminal and then press <Enter>:

sudo apt-get install lamp-server^

Important Note: No, that's not a typo error. Please make sure to include the caret (^). The command will not work without it.

3. The Terminal will then ask you for you're "User Account" password, type it and then press <Enter>

4. Now the apt package manager will show all the packages that need to be installed, press "Y" to accept, press <Enter>, to confirm that you want to install them.

5. Now the packages will be downloaded and installed, when done you will then be prompted to change the password for the "root" user on the MySQL database, enter the password of your choice (Please make sure that you choose tough password).

6. You'll be prompted to enter it a second time to confirm, after you confirm your password, apt will continue to install the rest of the packages.

7. When done close the Terminal window and restart the computer.

Congratulations, your LAMP installation is now complete!


That was the easy part, now you need to make bellow mentioned configuration to make your development environment easy to work with.


Test Apache:

1. Open your favourite web browser and enter the following address:

[http://localhost/](http://localhost/). 

2. You should see a web page that says "It Works!"

3. Now restart Apache by typing the following command into the Terminal window.

sudo /etc/init.d/apache2

4. You get the following message “Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName”

5. To fix that problem, you need to edit the httpd.conf file. Open the terminal and type: 

sudo gedit /etc/apache2/httpd.conf

6. By default httpd.conf file will be blank. Now, simply add the following line to the file:

ServerName localhost

7. Save the file and exit from gEdit.

8. Finally restart the server by typing following command into the terminal:

sudo /etc/init.d/apache2 restart


Now we have to edit "/etc/apache2/sites-enabled" in order to SEO (URL re-writes) to work through .htaccess file, please follow this steps.

1. Enter the following command in terminal:

sudo a2enmod rewrite

2. Now restart the server by typing following command into the terminal:

sudo /etc/init.d/apache2 restart

3. Now open 000-default file by issuing following command:

gksudo gedit /etc/apache2/sites-enabled/000-default

3. The file will open in gedit text editor please make following changes on 11th line AllowOverride None to AllowOverride All, save the file and exit

4. Restart Apache you are now done.


Test PHP
Now it is time to test the PHP installation. 

1. You'll need to create a file in /var/www called testphp.php, open the terminal and enter:

sudo gedit /var/www/testphp.php

2. This will open up a file called testphp.php, Copy/Paste this following line into the testphp.php file:

<?php phpinfo(); ?>

3. Hit Ctrl+S to save the file, hit Alt+F4 to exit.

4. Next, restart Apache with the following terminal command:

sudo /etc/init.d/apache2 restart

5. Now open you're web browser and type the following web address:

[http://localhost/testphp.php](http://localhost/testphp.php)

6. Now you should see a page displaying detailed PHP configuration.

Congrats you have now tested and configured both Apache and PHP!


Configure MySQL

1. Since we are installing LAMP for a web development environment, we want the MySQL database to be bound to the localhost IP address that is 127.0.0.1 for your system, you can verify localhost IP address with this terminal command:

cat /etc/hosts | grep localhost

2. You should see a line that looks like this:

127.0.0.1	localhost

3. You'll now want to verify that the correct bind address is set up in MySQL's my.cnf file, enter following command and hit <Enter>:

cat /etc/mysql/my.cnf | grep bind-address

4. You should see a line that looks like this:

bind-address	= 127.0.0.1

This line shows that MySQL database is bound to the localhost IP address 127.0.0.1


Optional Step: If you want other computers on your network to view the MySQL server you have created, you must first edit the "Bind Address" in "my.cnf" file. 

1. Open the Terminal and enter the following command:

gksudo gedit /etc/mysql/my.cnf

2. Find and change the line: bind-address = 127.0.0.1 to your IP address.


Install phpMyAdmin

You don't need to install phpMyAdmin to work with MySQL, but it's a much easier way to deal with MySQL database if you're not familiar with MySQL's commands. 

1. You can install phpMyAdmin from the command line with following command:

sudo apt-get install libapache2-mod-auth-mysql phpmyadmin

2. Now the apt package manager will show all the packages that need to be installed, press "Y" to accept, press <Enter>, to confirm that you want to install them.

3. Now the packages will be downloaded and installed

4. Next the installation will prompt you to select a web server for automatic configuration. This is important! Use the space bar on your keyboard to select apache2. Make sure there's a * next to apache2 and then hit <Enter>.

5. The next screen will explain some information about database configuration, hit the <Enter> key to move on.

6. Another screen will come up asking if you want to configure a new database called dbconfig-common, since this is a fresh installation, use the <Tab> key to select "Yes" and hit <Enter>.

7. Now you will be prompted to enter the MySQL root password, enter the MySQL root password that you created earlier, hit <Tab> to select Ok and hit <Enter>.

8. Now you will be prompted to enter a MySQL application password for phpmyadmin, you can hit <Enter> and a random password will be generated, but it is recommended that you enter password of your choice, I chose to use the same password that I used for the root MySQL password.

9. If you enter your own password, a password confirmation screen will come up, confirm your password.

10.Now open terminal and type:

gksudo gedit /etc/phpmyadmin/config.inc.php

11.Find and edit this line 
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysqli';
To
$cfg['Servers'][$i]['extension'] = 'mysql';

12.Now find the following line,
"$cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';"
and add the following line bellow it,
"$cfg['Servers'][$i]['tracking'] = 'pma_tracking';"

Your phpMyAdmin installation and configuration is now complete, but before doing any thing just restart the computer for the changes to take effect.


Testing phpMyAdmin

1. Open your web browser and enter the following address:

[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

2. Log in with the user-name "root" and the password that you created earlier.


Install CURL:

1. Simply type following command in terminal:

sudo apt-get install php5-curl

2. Restart Apache

Congratulations, you're now ready to start building your local website.

---

### Post by s.a.patil on 2011-05-04
Hi everyone, today I'm installing Ubuntu 11.04, and I shall post whether this same guide hold good or not.

---

### Post by rockvilla on 2011-11-23
Thanks for awesome tutorial helped a lot :guitar:

---

### Post by mikegior on 2011-11-23
Thanks for the tutorial, this will come in handy!:)

---

### Post by mastablasta on 2011-11-23
why not just use tasksel? [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by whyDoIHaveToRegister2012 on 2012-01-12
Did not get this msg: 

4. You get the following message “Could not reliably determine the  server’s fully qualified domain name, using 127.0.1.1 for ServerName”

I got this:

* Usage: /etc/init.d/apache2 {start|stop|graceful-stop|restart|...

But, I went on to the next step:

5. To fix that problem, you need to edit the httpd.conf file. Open the terminal and type: 

sudo gedit /etc/apache2/httpd.conf

And, then I got:

sudo gedit /etc/apache2/httpd.conf: command not found

What do I do now? I followed the instructions to the letter. Should I just continue with the next step. Why am I reconfiguring Apache? Seems to me it should install correctly the first time.

---

### Post by McDivvy on 2012-02-28
Excellent guide with the exception of the mistake mentioned below!  

whyDoIHaveToRegister2012, this may be because the line should have read:

```
sudo /etc/init.d/apache2 restart 
```to restart, instead of 

```
sudo /etc/init.d/apache2
```As to the "Command not Found" for 

```
sudo gedit /etc/apache2/httpd.conf
```It works fine on a fresh install of 11.10 server for me.  I would guess either a typo at your end or gedit is not installed - try running 

```
sudo apt-get install gedit
```first then trying again.

Oh, and this guide is to show you how to do it manually(ish!) - you can do the initial install of LAMP during installation of server, or you can use tasksel to do it at a later date.  This is a command line method.  And the reason we're "reconfiguring" Apache is to make sure things are installed correctly and also so that we know what's what with the different parts of it.   

Find and change the line: bind-address = 127.0.0.1 to your IP address

Is especially handy - you can now access the mySQL DB from across the network by pointing to the LAMP server's IP address in you connection string.

---

