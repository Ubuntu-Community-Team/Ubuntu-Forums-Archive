---
title: "WordPress disaster - various issues with install"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by SuaSwe on 2010-10-26
Hi all,

I'm just in the middle of configuring WordPress on my Ubuntu Server (8.10), and unfortunately I am running into all kinds of issues in doing so.

First to tell you what problem I'm having: whenever I type in the URL where index.php seems to be located ([http://www.domain.com/wordpress/index.php](http://www.domain.com/wordpress/index.php)), I get the following message:

> 
You have chosen to open
index.php
which is a: PHP file
from [http://www.domain.com](http://www.domain.com)

What should Firefox do with this file?


I gather that this suggests that php is not installed (properly) on the server, but I did when following the Ubuntu Documentation instructions (here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)), like so:

```

sudo aptitude install wordpress php5-gd 
```

Note however that due to an earlier ****-up I did strip and reinstall LAMP and WordPress at one point (although this does not seem to have cleared the config files for any of the packages, I noted). 

Does anyone have any ideas why php isn't loading?

---

### Post by DooM55 on 2010-10-26
do u need  run localhost on your system or u lose your Cpanel / site  on domain.com


[COLOR=#000000]Please explain more[/COLOR]:popcorn:

---

### Post by SuaSwe on 2010-10-26
Right, slight update here: found the solution right under my nose, on the Ubuntu Documentation site:

```

sudo aptitude purge libapache2-mod-php5
sudo aptitude install libapache2-mod-php5

```

So I now got a proper HTML response from Firefox. However, once I got that far it started to give me errors like this:

```

Warning: require_once(/etc/wordpress/wp-settings.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 27

```

Which I'm presuming was because the WordPress directory isn't /etc/wordpress but /var/www/wordpress. Created a symlink and it now does take me somewhere... Unfortunately, however, this somewhere isn't a configuration page but the no-ip.org search portal site. :( I used to have a no-ip.org domain back in the day, so I'm wondering if I configured my server to this end at some point and forgot about it.

Anyone have any ideas on how to completely wipe WordPress/Apache/PHP/mySQL configs, including configuration files? Think I'm going to need to start over here!

---

### Post by SuaSwe on 2010-10-26
DooM55: I have a domain, and am connecting to the server from a client machine, not from the server itself (no GUI installed on there). :)

---

### Post by DooM55 on 2010-10-26
ok 

install apatch / phpmyadmin /mysql  on lunix

```

 sudo aptitude install mysql-server mysql-client

 sudo aptitude install apache2

```after that open [http://localhost/](http://localhost/)

you will see 
It works!

after that
```


sudo aptitude install php5 libapache2-mod-php5

 sudo /etc/init.d/apache2 restart

sudo chmod 777 -R /var/www

```search module

```
sudo aptitude search php5
```    sudo aptitude install <module_name>


```


 sudo /etc/init.d/apache2 restart

  sudo aptitude install phpmyadmin

```Web server to reconfigure automatically  Apache2
Configure database for phpmyadmin with dbconfig-common?&#1548;  no


open this file
```
sudo gedit /etc/apache2/apache2.conf
```add this line

Include /etc/phpmyadmin/apache.conf

save file

```
sudo /etc/init.d/apache2 restart
```:guitar:

and now Go to 
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

:KS

---

### Post by SuaSwe on 2010-10-26
Hiya,

Does that still work even though I'm accessing the server from a client machine? Wouldn't [http://localhost](http://localhost) attempt to direct me to 127.0.0.1 of the client machine, not the server? 

Have just tried anyway and am getting '404 Not Found' on [http://localhost/phpmyadmin](http://localhost/phpmyadmin).. Also it's WordPress I'm having trouble with - Apache is actually working, in that I can get to [http://www.mydomain.com/index.html](http://www.mydomain.com/index.html). :)

---

### Post by DooM55 on 2010-10-26
to solve this  problem

Warning: require_once(/etc/wordpress/wp-settings.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 27  



 delete wp-config

and reinstall wordpress

---

### Post by SuaSwe on 2010-10-26
Hi there DooM55,

That issue was resolved - it was looking for a file in /etc/wordpress which was actually located in /var/www/wordpress. :)

Problem was that even when it found the file it redirected to the wrong place. I've now completely wiped all config and am attempting it anew.

---

### Post by DooM55 on 2010-10-26
> **SuaSwe said:**
> Hi there DooM55,

That issue was resolved - it was looking for a file in /etc/wordpress which was actually located in /var/www/wordpress. :)

Problem was that even when it found the file it redirected to the wrong place. I've now completely wiped all config and am attempting it anew.

[COLOR=#000000]Well I'm with you 
[/COLOR][COLOR=#000000]Tell me what happen with you[/COLOR]

Sorry but I have weak English language :KS

---

### Post by SuaSwe on 2010-10-26
Haha, you're fine!

Have managed to get it working now. :) Procedure below, in case someone comes along with similar issues. 

Completely removed all packages:

```

sudo aptitude remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

sudo aptitude purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

```

Found and removed all folders relating to:
- apache2
- php
- mysql

Reinstalled LAMP:

```

sudo tasksel install lamp-server

```

Tested php:

```

sudo echo "<?php phpinfo(); ?>" > /var/www/testphp.php

```

Tried on client's Firefox: [http://192.168.0.130/testphp.php](http://192.168.0.130/testphp.php)

Result:
"You have chosen to open index.php, which is a: PHP file"

Argh! Nearing insanity now...

Purged and reinstalled libapache2-mod-php5:

```

sudo aptitude purge libapache2-mod-php5
sudo aptitude install libapache2-mod-php

Checked that php5 is enabled (it was) and restarted apache2 (OK):

[code]
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

Once again, on client: [http://192.168.0.130/testphp.php](http://192.168.0.130/testphp.php) ... And finally it loads OK!

Downloaded latest release of WordPress from [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz), moved into /var/www/ and unzipped. Set ownership of folder:

<code>
sudo chown -R myuser:myuser wordpress
</code>

Configured mySQL database for use by server:

```

mysql -u root -p
mysql> CREATE DATABASE databasename;
mysql> CREATE USER bloguser;
mysql> SET PASSWORD FOR bloguser = PASSWORD("blogpassword");
mysql> GRANT ALL PRIVILEGES ON databasename.* TO "bloguser"@"localhost" IDENTIFIED BY "blogpassword";
mysql> FLUSH PRIVILEGES;
mysql> quit

```

Opened /var/www/wordpress/wp-config.php and updated the following bits:

```

    * DB_NAME: databasename
    * DB_USER: bloguser
    * DB_PASSWORD: blogpassword
    * DB_HOST: localhost

```

Generated secure keys here: [https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/) - then added them to wp-config.php where specified.

Back to client, now testing WordPress functionality: [http://192.168.0.130/wordpress](http://192.168.0.130/wordpress)

Response: "Your PHP installation appears to be missing the MySQL extension which is required by WordPress."

Starting mysql in case it was stopped, installed php5-mysql and restarted Apache:

```

sudo /etc/init.d/mysql start
sudo aptitude install php5-mysql
sudo /etc/init.d/apache2 restart

```

And FINALLY, finally, WordPress is loading the admin pages! Hurrah! :D Now all I need to do is figure out how to move it from [www.domain.com/wordpress](www.domain.com/wordpress) to [www.domain.com/otherdirectory](www.domain.com/otherdirectory)...!

---

### Post by DooM55 on 2010-10-26
very Good :P

---

