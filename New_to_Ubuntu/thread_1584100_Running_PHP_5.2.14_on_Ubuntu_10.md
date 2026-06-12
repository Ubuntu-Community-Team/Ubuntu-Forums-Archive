---
title: "Running PHP 5.2.14 on Ubuntu 10"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by tanzimshaikh on 2010-09-28
[SIZE=2]Hi ...
I am very new to open source. Directly coming from Windows background.
I have installed Ubuntu 10.04 and then have run the following sudo apt-get commands to install Apache2 and MySQL. Apache2 and MySQL is working fine as I tested them.
However if I do the same then I will be able to install PHP 5.3 which I don't want. Hence I went to the source of PHP and downloaded PHP 5.2.14. The reason I want PHP 5.2.14 is because MediaWiki doesn't work with PHP 5.3 due to some bug.

My problem started here :( ... I run the ./configure command along with --with Apache2 and --with MySQL commands that I copy/paste from a site (I don't remember the site nor the command).
Then I run the following make, then make test, then make install, then clean install.:)

Hoping that everything will be working fine when I tried to run php file which contains phpinfo(); from /var/www the firefox is asking to open the file rather than running the php script.:(

What shall I do to make sure that my system is running fine with Apache2, MySQL and PHP 5.2.14, all integrated together so that I may start my development ASAP. :?

Thank you
Tanzim Akhtar[/SIZE]

---

### Post by Apollo87 on 2010-09-28
Hello,

Its possible that apache does not have a handler set that tells it to parse .php file extensions as php files.  Try opening up your httpd.conf file and adding this line to it:

```
AddHandler application/x-httpd-php .php .phtml
```

Then restart apache and try running that script again from the web.

If you can get your hands on that configure command you ran as well, that would be nice.

---

### Post by tanzimshaikh on 2010-09-29
[FONT=Trebuchet MS][SIZE=2]Thank you Apollo87.
Since I am very new to open source technology I was expecting a step-by-step instructions because it took me a while to get around the commands to edit httpd.conf. However I came across an article which talks about apache2.conf.

Can you please rewrite the commands that I should follow now to make it work?

Thank you once again. :)
[/SIZE][/FONT]

---

### Post by tanzimshaikh on 2010-10-08
[FONT=Verdana][SIZE=2]Alhamdulillaah (All thanks and praise to Allaah Alone) ... I have been able to achieve what I wanted.

I went to the following site: [http://antojose.com/content/how-install-set-apache-php-5-2-mysql-lamp-development-environment-drupal-ubuntu-10-04-lucid-ly](http://antojose.com/content/how-install-set-apache-php-5-2-mysql-lamp-development-environment-drupal-ubuntu-10-04-lucid-ly) and followed to the core.

Now PHP 5.2.10 is running with Apache2 on Ubuntu 10.04. :P
[/SIZE][/FONT]

---

### Post by ProntoAnthony on 2010-10-09
I followed the detailed instructions, too. my html pages work fine when I browse to [http://localhost/index.htm](http://localhost/index.htm), for example.

No such luch with php scripts. Apache doesn't know how to interpret/display  [http://localhost/index.php](http://localhost/index.php) and so it instead just downloads it to the browser. 

Adding the line:

```
AddHandler application/x-httpd-php .php .phtml
```
to the httpd.conf file had no effect on the problem.

edit*****

I reloaded the browser, restarted apache, and all is well.
Praise Jesus!!


-Anthony

---

### Post by asg8516 on 2010-10-21
ProntoAnthony,

This is Anto Jose of antojose.com. 

Ubuntu is asking for downloading the php file because, from release 10.04, by default, php scripts in user directories are disabled from running (I heard it's the same for debian as well)..

To overcome that, you could use the following:
Open up the php5.conf file,
    ```
sudo gedit /etc/apache2/mods-available/php5.conf
```
and uncomment the following lines:
```

  #<IfModule mod_userdir.c> 
  #  <Directory /home/*/public_html> 
  #    php_admin_value engine Off 
  #  </Directory> 
  #</IfModule> 
```
to look like this:
```
  
   <IfModule mod_userdir.c> 
     <Directory /home/*/public_html> 
       php_admin_value engine Off 
     </Directory> 
   </IfModule> 

```

Save and exit.

Now restart apache daemon by 
```
sudo /etc/init.d/apache2 restart
```

That should do the trick! :)


Cheers,
Anto

P.S.: I will update the howto on antojose.com.

> **ProntoAnthony said:**
> I followed the detailed instructions, too. my html pages work fine when I browse to [http://localhost/index.htm](http://localhost/index.htm), for example.

No such luch with php scripts. Apache doesn't know how to interpret/display  [http://localhost/index.php](http://localhost/index.php) and so it instead just downloads it to the browser. 

Adding the line:

```
AddHandler application/x-httpd-php .php .phtml
```
to the httpd.conf file had no effect on the problem.

edit*****

I reloaded the browser, restarted apache, and all is well.
Praise Jesus!!


-Anthony

---

### Post by ProntoAnthony on 2010-10-22
No, that did not work. The lines were already uncommented. Restarting apache had no effect.

That just means that I'm still running php 5.2 instead of 5.3. No big deal. Thanks for trying to help.

---

### Post by VcDeveloper on 2010-10-31
> **tanzimshaikh said:**
> [FONT=Verdana][SIZE=2]Alhamdulillaah (All thanks and praise to Allaah Alone) ... I have been able to achieve what I wanted.

I went to the following site: [http://antojose.com/content/how-install-set-apache-php-5-2-mysql-lamp-development-environment-drupal-ubuntu-10-04-lucid-ly](http://antojose.com/content/how-install-set-apache-php-5-2-mysql-lamp-development-environment-drupal-ubuntu-10-04-lucid-ly) and followed to the core.

Now PHP 5.2.10 is running with Apache2 on Ubuntu 10.04. :P
[/SIZE][/FONT]

I followed the instruction, but I running 10.10 Maverick.  How do I check to see if it was successful, because I still see 5.3 in Synaptic Package Manager as well as in the Package|Force Version Dialog Box dropdown?

.....I have not installed anything yet!...

---

### Post by asg8516 on 2010-11-08
antojose.com now has released a fully pre-configured LAMP Development environment based on Ubuntu 10.04, by the name FreedomX Linux. :P

See [www.freedomx.in](www.freedomx.in) for details.

---

