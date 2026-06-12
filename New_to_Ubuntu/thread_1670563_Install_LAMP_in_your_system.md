---
title: "Install LAMP in your system"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-01-19
**Install Apache**
To start off we will install Apache.

1. Open up the Terminal (Applications > Accessories > Terminal).

2. Copy/Paste the following line of code into Terminal and then press enter:

*sudo apt-get install apache2*


**Testing Apache**

To make sure everything installed correctly we will now test Apache to ensure it is working properly.

1. Open up any web browser and then enter the following into the web address:

[http://localhost/](http://localhost/)

You should see a folder entitled apache2-default/. Open it and you will see a message saying "It works!" , congrats to you!

**Install PHP**

In this part we will install PHP 5.

Step 1. Again open up the Terminal (Applications > Accessories > Terminal).

Step 2. Copy/Paste the following line into Terminal and press enter:

sudo apt-get install php5 libapache2-mod-php5

Step 3. In order for PHP to work and be compatible with Apache we must restart it. Type the following code in Terminal to do this:

sudo /etc/init.d/apache2 restart

**Test PHP**

To ensure there are no issues with PHP let's give it a quick test run.

Step 1. In the terminal copy/paste the following line:

sudo gedit /var/www/testphp.php

This will open up a file called phptest.php.

Step 2. Copy/Paste this line into the phptest file:

<?php phpinfo(); ?>

Step 3. Save and close the file.

Step 4. Now open you're web browser and type the following into the web address:

[http://localhost/testphp.php](http://localhost/testphp.php)

**Install MySQL:**

 sudo apt-get install mysql-server mysql-client

Here you will be asked to enter root password for MySql



Now just restart Apache and you are all set!

sudo /etc/init.d/apache2 restart

---

### Post by indytim on 2011-01-19
-Or 10 steps down to 2 :

> 
$sudo apt-get install tasksel
$sudo tasksel

Select the LAMP option (space bar) <enter>.   Respond to the password prompts and you're done.

:lolflag:

IndyTim / DataMan

---

### Post by daredevil82 on 2011-01-19
Or you can do all the install commands at once
```
sudo apt-get install apache2 php5 libapache2-mod-php5 mysql-server mysql-client
```

then do all your testing.  I did it this way the first time I installed LAMP, but tasksel is much easier.  It really should be included with ubuntu releases.

---

### Post by Paqman on 2011-01-19
+1 for tasksel, very handy little tool.

---

### Post by mastablasta on 2011-01-19
I would put it as launcher  under administration-> server creation :-)

---

