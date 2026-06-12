---
title: "Drupal 6 Clean URL issues!"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-09
Hi!
I have installed drupal 6 on my system. However the clean urls are not enabled. I googled around to find out that I have to do the below:-


[LIST=1]
[*]Ensure that mod_rewrite is enabled for Apache 2:
 [COLOR=#339933]%[/COLOR] sudo a2enmod rewrite
[*]Edit Apache 2 configuration to allow Drupal's .htaccess file to be used. In file **/etc/apache2/sites-enabled/000-default**, inside the tag **Directory /var/www/**, replace the line
AllowOverride none
with
AllowOverride All
[*]Restart Apache 2:
[COLOR=#339933]%[/COLOR] sudo [COLOR=#339933]/[/COLOR]etc[COLOR=#339933]/[/COLOR]init[COLOR=#339933].[/COLOR]d[COLOR=#339933]/[/COLOR]apache2 restart[FONT=Verdana][/FONT]
[/LIST]
But after modifying the file(000-default), I am unable to save it as it says I dont have permissions. Am quite new to the entire linux thing, so please helpp!

---

### Post by s_ø on 2010-04-09
you need to edit the file as root.
This file **/etc/apache2/sites-enabled/000-default** is a symlink to this file **/etc/apache2/sites-available/default**
I would edit the latter directly.
**sudo nano /etc/apache2/sites-available/default**

Also if you only need rewriterules tou should only **AllowOverride FileInfo** instead of **AllowOverride All**
The Apache docs has info on which directives are needed for what. [http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride)

Edit:
I think you should at least **Allowoverride FileInfo Options=Indexes,FollowSymLinks** to use drupals .htaccess directives.

---

### Post by vivek40 on 2010-04-09
[B]sudo nano /etc/apache2/sites-available/default

[/B]Thanks ! but what would the above command do

---

### Post by s_ø on 2010-04-09
[B]sudo nano /etc/apache2/sites-available/default
[/B]Will open **/etc/apache2/sites-available/default **with the [nano]("https://help.ubuntu.com/community/Nano") editor under root privileges. It wont change anything by it self, just open the file.

Edit:
If you open a terminal and use **ls -l /etc/apache2/sites-available** it will display details about file ownership. If a file is owned by root and is not world-writable you will need to use sudo to change it.
Read about terminal commands here [https://help.ubuntu.com/community/UsingTheTerminal#File%20&%20Directory%20Commands]("https://help.ubuntu.com/community/UsingTheTerminal#File%20&%20Directory%20Commands")
And about permissions here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If you prefer to edit files in a gui application you should use gksudo instead of sudo

Finally you should use service to start/stop dæmons.
**sudo service apache2 restart**

---

