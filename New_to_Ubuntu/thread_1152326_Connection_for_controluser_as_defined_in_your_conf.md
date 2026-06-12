---
title: "Connection for controluser as defined in your configuration failed."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by 007casper on 2009-05-07
updated to Jaunty Jackalope and one of my applications doesnt seem to access the database.  I checked the files, it seems like it does.  

I think during the upgrade something got deleted.  When I log into phpmyadmin... it says at the bottom "Connection for controluser as defined in your configuration failed."

???

please, help.  Thank you.

---

### Post by 007casper on 2009-05-07
I have checked etc/phpmyadmin/config.inc.php

controluser isnt uncommented.

should uncommented and change from &#8220;PMA&#8221; to &#8220;root&#8221;

??

---

### Post by 007casper on 2009-05-11
just create a mysql user through the terminal and grant all privileges that solves the problem

---

### Post by ubunter760 on 2009-05-28
I tried creating a new user, but that did not solve the problem for me.

---

### Post by ubunter760 on 2009-05-28
I found how to correct the problem in case anyone else needs a quick fix:

When recently upgrading my server to Ubuntu 9.04, phpMyAdmin was also upgraded to version 5.0.75. When I loaded up the new version, I was alarmed to find a new error message that read: Connection for controluser as defined in your configuration failed.

It turned out this error was due to the fact that version 5 of phpMyAdmin adds support for a new feature known as a linked-tables infrastructure. This infrastructure allows for new features such as bookmarks, comments, SQL-history, PDF-generation, and field contents transformation. The problem was that this new feature is enabled by default, with generic credentials set up for the controluser. If you don't have your database set up for the infrastructure, you will see the error. I have no use for these new features, so I'd rather just not mess with them. If you do want to enable the advanced features, here is an informative post about doing so on Ubuntu. If you just want to disable the linked-tables infrastructure, which is often the easiest and least intrusive way, just follow these steps:

   1. Type nano /etc/phpmyadmin/config.inc.php in the Linux terminal. You can substitute nano for vi or your favorite text editor.
   2. Find the two blocks of text that read:

      $cfg['Servers'][$i]['controluser'] = $dbuser;
      $cfg['Servers'][$i]['controlpass'] = $dbpass;

      one is near the top embedded in an if statement, and the other is towards the bottom. The text is not exactly the same for each block, but $cfg['Servers'][$i]['controluser'] is what matters. The block that is actually used by phpMyAdmin depends on your setup, but just for simplicity we will apply the change to both.
   3. Just comment out those four lines by adding a // in front of each one.
   4. Save, and the error should disappear next time you access phpMyAdmin. If you are still having trouble, feel free to post a comment.

---

### Post by konsty on 2009-05-29
Thanks, worked for me!

---

### Post by xjoywag on 2009-06-01
Maybe we should to change the following lines in 'config-db.php':
$dbuser='YOUR_USER_NAME'
$dbpass='YOUR_PASSWORD'
 
I see the same error at beginning, I modified those lines then no error show me again.

---

### Post by Andrew0493 on 2009-06-01
Worked for me as well. Thanks.

---

### Post by Stoneface on 2009-06-06
> **xjoywag said:**
> Maybe we should to change the following lines in 'config-db.php':
$dbuser='YOUR_USER_NAME'
$dbpass='YOUR_PASSWORD'
 
I see the same error at beginning, I modified those lines then no error show me again.

I upgraded to Jaunty and did uninstalled en reinstalled gnome and Ubuntu Desktop because of some problems. Now I can enter PHP Myadmin, but I get this warning:
Connection for controluser as defined in your configuration failed.

When I go to config.inc.php I see a blank file!? I entered:

$dbuser='YOUR_USER_NAME'
$dbpass='YOUR_PASSWORD'

It got all messed up. I did not find a config.db.php in /var/lib/phpmyadmin...

---

### Post by Stoneface on 2009-06-06
Found the file in /etc/phpmyadmin. Will change the user/pw there. Then I logged on again. Lay-out as all gone like the css was all gone. I reinstalled all. Now I see these warning/messages:

```
#0  PMA_sendHeaderLocation(http://localhost/phpmyadmin/index.php?token=dc2296b833fe47037618698da46c9a19) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```

The I entered MySQL from ssh and saw I do no longer have a database phpmyadmin! How am I going to fix this?

I even reinstalled phpmyadmin, but it does not seem to help en the same error keeps popping up :-(

P.S. All other database are still there.

[SIZE="4"]**I will start a new thread as this is no longer connected to earlier problem**[/SIZE]
[http://ubuntuforums.org/showthread.php?p=7414211]("http://ubuntuforums.org/showthread.php?p=7414211")

---

### Post by Stoneface on 2009-06-06
Well I removed it again from the terminal without removing the database as I could not remove it because I don't know the password. Then I reinstalled. It did work, but I got this feeback:
```
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using
             old-style, non-debconf prompting. Ugh!

             Please inform the package maintainer about this problem.
Replacing config file /etc/phpmyadmin/config-db.php with new version
dbconfig-common: flushing administrative password
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
invoke-rc.d: unknown initscript, /etc/init.d/apache not found.
invoke-rc.d: unknown initscript, /etc/init.d/apache-ssl not found.
invoke-rc.d: unknown initscript, /etc/init.d/apache-perl not found.
Lighttpd not installed, skipping
invoke-rc.d: unknown initscript, /etc/init.d/lighttpd not found.
```
Then I went to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) entered phpmyadmin as user and the password. Then I got this same persistent error:
```
#0  PMA_sendHeaderLocation(http://localhost/phpmyadmin/index.php?token=4881d3e9fffb5ad42437e6c41e9a5ddd) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```

I went into mysql from ssh again using mysql -u -p and saw that I do have a database phpmyadmin now. Now I just need to get into it without these errors!!

---

### Post by Stoneface on 2009-06-06
I went into /var/lib/phpmyadmin/config.inc.php and saw no data in the file... Is that an issue?

---

### Post by Stoneface on 2009-06-07
I went to /etc/phpmyadmin/config.inc.php and found data:
```
<?php
/**
 * Debian local configuration file
 *
 * This file overrides the settings made by phpMyAdmin interactive setup
 * utility.
 *
 * For example configuration see /usr/share/doc/phpmyadmin/examples/config.default.php.gz
 *
 * NOTE: do not add security sensitive data to this file (like passwords)
 * unless you really know what you're doing. If you do, any user that can
 * run PHP or CGI on your webserver will be able to read them. If you still
 * want to do this, make sure to properly secure the access to this file
 * (also on the filesystem level).
 */

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Read configuration from dbconfig-common */
require('/etc/phpmyadmin/config-db.php');

/* Configure according to dbconfig-common if enabled */
if (!empty($dbname)) {
    /* Authentication type */
    $cfg['Servers'][$i]['auth_type'] = 'cookie';
    /* Server parameters */
    if (empty($dbserver)) $dbserver = 'localhost';
    $cfg['Servers'][$i]['host'] = $dbserver;

    if (!empty($dbport)) {
        $cfg['Servers'][$i]['connect_type'] = 'tcp';
        $cfg['Servers'][$i]['port'] = $dbport;
    }
    //$cfg['Servers'][$i]['compress'] = false;
    /* Select mysqli if your server has it */
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    /* Optional: User for advanced features */
    $cfg['Servers'][$i]['controluser'] = $dbuser;
    $cfg['Servers'][$i]['controlpass'] = $dbpass;
    /* Optional: Advanced phpMyAdmin features */
    $cfg['Servers'][$i]['pmadb'] = $dbname;
    $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
    $cfg['Servers'][$i]['relation'] = 'pma_relation';
    $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
    $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
    $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
    $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
    $cfg['Servers'][$i]['history'] = 'pma_history';
    $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

    /* Advance to next server for rest of config */
    $i++;
}

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'pma';
// $cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';


```

With config-db.php data I do try to logon, but I keep on getting the same error:

```
#0  PMA_sendHeaderLocation(http://localhost/phpmyadmin/index.php?token=7e5ae2ccb9f77209cec3cf5d93bb835a) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```

I would appreciate anybody's help to get phpmyadmin going today. It worked before and MySQL, Apache and PHP still do...

---

### Post by cmwslw on 2009-06-07
> **Stoneface said:**
> I went to /etc/phpmyadmin/config.inc.php and found data:
```
<?php
/**
 * Debian local configuration file
 *
 * This file overrides the settings made by phpMyAdmin interactive setup
 * utility.
 *
 * For example configuration see /usr/share/doc/phpmyadmin/examples/config.default.php.gz
 *
 * NOTE: do not add security sensitive data to this file (like passwords)
 * unless you really know what you're doing. If you do, any user that can
 * run PHP or CGI on your webserver will be able to read them. If you still
 * want to do this, make sure to properly secure the access to this file
 * (also on the filesystem level).
 */

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Read configuration from dbconfig-common */
require('/etc/phpmyadmin/config-db.php');

/* Configure according to dbconfig-common if enabled */
if (!empty($dbname)) {
    /* Authentication type */
    $cfg['Servers'][$i]['auth_type'] = 'cookie';
    /* Server parameters */
    if (empty($dbserver)) $dbserver = 'localhost';
    $cfg['Servers'][$i]['host'] = $dbserver;

    if (!empty($dbport)) {
        $cfg['Servers'][$i]['connect_type'] = 'tcp';
        $cfg['Servers'][$i]['port'] = $dbport;
    }
    //$cfg['Servers'][$i]['compress'] = false;
    /* Select mysqli if your server has it */
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    /* Optional: User for advanced features */
    $cfg['Servers'][$i]['controluser'] = $dbuser;
    $cfg['Servers'][$i]['controlpass'] = $dbpass;
    /* Optional: Advanced phpMyAdmin features */
    $cfg['Servers'][$i]['pmadb'] = $dbname;
    $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
    $cfg['Servers'][$i]['relation'] = 'pma_relation';
    $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
    $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
    $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
    $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
    $cfg['Servers'][$i]['history'] = 'pma_history';
    $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

    /* Advance to next server for rest of config */
    $i++;
}

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'pma';
// $cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';


```

With config-db.php data I do try to logon, but I keep on getting the same error:

```
#0  PMA_sendHeaderLocation(http://localhost/phpmyadmin/index.php?token=7e5ae2ccb9f77209cec3cf5d93bb835a) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```

I would appreciate anybody's help to get phpmyadmin going today. It worked before and MySQL, Apache and PHP still do...

Your problem has to do with the fact that config.inc.php is empty. [This thread]("http://ubuntuforums.org/showthread.php?t=891543&page=2") describes your problem. It looks like you need to reinstall phpmyadmin:

```
sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin
```

-hope this helps, Cory

---

### Post by Stoneface on 2009-06-08
config-db.php has data:

```
<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/phpmyadmin.conf
## by /usr/sbin/dbconfig-generate-include
## Sun, 07 Jun 2009 10:43:53 +0400
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='user_name';
$dbpass='p_w';
$basepath='';
$dbname='phpmyadmin2';
$dbserver='';
$dbport='';
$dbtype='mysql';
?>
```

and so has config.inc.php:

```
<?php
/**
 * Debian local configuration file
 *
 * This file overrides the settings made by phpMyAdmin interactive setup
 * utility.
 *
 * For example configuration see /usr/share/doc/phpmyadmin/examples/config.default.php.gz
 *
 * NOTE: do not add security sensitive data to this file (like passwords)
 * unless you really know what you're doing. If you do, any user that can
 * run PHP or CGI on your webserver will be able to read them. If you still
 * want to do this, make sure to properly secure the access to this file
 * (also on the filesystem level).
 */

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Read configuration from dbconfig-common */
require('/etc/phpmyadmin/config-db.php');

/* Configure according to dbconfig-common if enabled */
if (!empty($dbname)) {
    /* Authentication type */
    $cfg['Servers'][$i]['auth_type'] = 'cookie';
    /* Server parameters */
    if (empty($dbserver)) $dbserver = 'localhost';
    $cfg['Servers'][$i]['host'] = $dbserver;

    if (!empty($dbport)) {
        $cfg['Servers'][$i]['connect_type'] = 'tcp';
        $cfg['Servers'][$i]['port'] = $dbport;
    }
    //$cfg['Servers'][$i]['compress'] = false;
    /* Select mysqli if your server has it */
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    /* Optional: User for advanced features */
    $cfg['Servers'][$i]['controluser'] = $dbuser;
    $cfg['Servers'][$i]['controlpass'] = $dbpass;
    /* Optional: Advanced phpMyAdmin features */
    $cfg['Servers'][$i]['pmadb'] = $dbname;
    $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
    $cfg['Servers'][$i]['relation'] = 'pma_relation';
    $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
    $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
    $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
    $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
    $cfg['Servers'][$i]['history'] = 'pma_history';
    $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

    /* Advance to next server for rest of config */
    $i++;
}

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'pma';
// $cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';


```

So the problem must be elsewhere? Maybe the user I have does not have rights to the database? It is just that these errors don't lead me anywhere and I have reinstalled it twice now..

---

### Post by Sizzlintrumpet on 2009-06-26
I'm so excited, my first post on Ubuntu Forms where I feel can really help. :D I too had this problem and was fustrated. This problem was cased by either deleting the user "phpmyadmin" or you changed phpmyadmin's password.

If you deleted them from the table Users in the MySQL database you have to reconfigure the settings by typing in the terminal 

```
sudo dpkg-reconfigure phpmyadmin
```

Now follow the wizard and recreate the user phpmyadmin (set as default), when complete you can view their password by typing in the terminal

```
sudo gedit /etc/phpmyadmin/config-db.php
```

With that information goto [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and login using phpmyadmin as the username and the password defined in the config-db.php

Okay so from phpmyadmin you can change your password, but if you do you must also change the password in config-db.php by using the terminal and going to. 

```
sudo gedit /etc/phpmyadmin/config-db.php
```


I hope this helps you out, this should also enable the relationship view in the phpmyadmin menu as well which is useful for referential integrity between tables.

---

### Post by Stoneface on 2009-06-26
Unfortunately I waited so long that I decided to to a basic local installation of the entire package in var/www/ This one will not be updated automagically though. But I got so frustrated and decided to follow some other Ubuntu forum member on this (see [http://ubuntuforums.org/showthread.php?p=7521019#post7521019](http://ubuntuforums.org/showthread.php?p=7521019#post7521019)). I will go through your details and I hope there is something there I missed. Then I might uninstall and do my sixth installation via apt-get.
Question: How do you delete a user in the database using the MySQL command line?

---

### Post by Sizzlintrumpet on 2009-06-26
I don't know how to delete using the MySQL command line, but you can do it through phpmyadmin.

Click on the mysql database
Click on the user table

From there you can view all the users. You can make changes, but note that the password field is encrypted.

---

### Post by gleble on 2009-06-27
I have the same problem. My config.inc.php is different to those above

```
<?php
/*
 * This is needed for cookie based authentication to encrypt password in
 * cookie
 */
$cfg['blowfish_secret'] = 'xampp'; /* YOU SHOULD CHANGE THIS FOR A MORE SECURE COOKIE AUTH! */

/*
 * Servers configuration
 */
$i = 0;

/*
 * First server
 */
$i++;

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '';
$cfg['Servers'][$i]['AllowNoPasswordRoot'] = true;

/* User for advanced features */
$cfg['Servers'][$i]['controluser'] = 'pma';
$cfg['Servers'][$i]['controlpass'] = '';

/* Advanced phpMyAdmin features */
$cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
$cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
$cfg['Servers'][$i]['relation'] = 'pma_relation';
$cfg['Servers'][$i]['table_info'] = 'pma_table_info';
$cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
$cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
$cfg['Servers'][$i]['column_info'] = 'pma_column_info';
$cfg['Servers'][$i]['history'] = 'pma_history';
$cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

?>
```
Is  there anything I can comment out that might help?

---

### Post by phillw on 2009-09-23
> **Sizzlintrumpet said:**
> I'm so excited, my first post on Ubuntu Forms where I feel can really help. :D I too had this problem and was fustrated. This problem was cased by either deleting the user "phpmyadmin" or you changed phpmyadmin's password.

If you deleted them from the table Users in the MySQL database you have to reconfigure the settings by typing in the terminal 

```
sudo dpkg-reconfigure phpmyadmin
```Now follow the wizard and recreate the user phpmyadmin (set as default), when complete you can view their password by typing in the terminal

```
sudo gedit /etc/phpmyadmin/config-db.php
```With that information goto [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and login using phpmyadmin as the username and the password defined in the config-db.php

Okay so from phpmyadmin you can change your password, but if you do you must also change the password in config-db.php by using the terminal and going to. 

```
sudo gedit /etc/phpmyadmin/config-db.php
```I hope this helps you out, this should also enable the relationship view in the phpmyadmin menu as well which is useful for referential integrity between tables.


He he ... will you marry me ?!!!:lolflag:

Thanks, I was hacked a while back and did a re-install - this error message kept cropping up. Oddly enough the root login worked with the new p/w - obviously (now) it was the phpmyadmin internal bit that had not been restored.

Phill.

P.S. - the answer here is top of the list for google search
MySQL Connection for controluser as defined in your configuration failed.

---

### Post by casper_2095 on 2009-10-06
It's just as easy to create the user as it is to comment out the possibility... (use your own root password on this first line)

john@lappy:/etc/phpmyadmin$ mysql --user=root --password=password
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 231
Server version: 5.0.75-0ubuntu10.2 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create user 'phpmyadmin'@'localhost' identified by 'password';
Query OK, 0 rows affected (0.03 sec)

mysql> grant all privileges on *.* to 'phpmyadmin'@'localhost' with grant option;
Query OK, 0 rows affected (0.00 sec)

Worked for me.

---

### Post by swiftsam on 2009-11-03
For what it's worth, I had these problems when phpmyadmin was upgraded as I moved from 8.04 to 9.10.  This thread was great, but my attention span must be too short today to make all of the changes appropriately.

What did work, and was super easy was to completely remove phpmyadmin and reinstall it.

```

sudo apt-get remove --purge phpmyadmin
sudo apt-get install phpmyadmin

```

Obviously not good if you have lots of customizations in your config files, but worked like a charm for me.

---

### Post by matt_007 on 2009-11-26
Hi guys , i recently had the exact problem after setting up mysql database security/Pma account . 
I tried a number of things , and this is what worked for me : 

-xampp/phpmyadmin/config.inc.php 

/* User for advanced features */
$cfg['Servers'][$i]['controluser'] = 'pma';   
$cfg['Servers'][$i]['controlpass'] = '';  

-Added 'root' or your 'user' in place of 'pma' 
-And put the password in for the root account.

 Maybe this works because you are defining the 'root' account which has all the privileges , 
and the reason that warning comes up is because 'pma' account has no privileges set?? 

Or it could be that 'Pma' does not have the password verified as you can see above , or if you added a password for the 'pma' account in the mysql/privileges tab , and it has not been updated in the config.inc.php. 

If  i am completely wrong , i am a newbie at this   :(

---

### Post by Annelize on 2010-07-14
I have been trying to install LAMP server on Ubuntu 10.04 but having difficulty. The error message that comes up in my browser is "Cannot start session without errors, please check errors given in your  PHP and/or webserver log file and configure your PHP installation  properly." Despite reinstalling php, as suggested in this thread, it is still not working. 

Help would be much appreciated as I am not too familiar with Linux.
Thank you!

---

### Post by Dngrsone on 2010-07-26
I just ran into this problem after an update to MySQL (running 10.4 AMD-64).  Turns out the problem was that MySQL was not running.

To get it running (at least for the current session) try this in a terminal:

```
 sudo service mysql start
```

---

### Post by tagnu on 2010-09-23
Hi all,   

I had the same error after installing lampp on a new ubuntu box.  

Running 
>  mysqlmysqladmin -u root -p version Returned  
>  UNIX socket        /var/run/mysqld/mysqld.sock Which meant, there was another instance of mysql running on the system. 

Got it resolved after stopping the current server and running lampp again.
>  sudo service mysql stop 
sudo /opt/lampp/lampp start Thank you.

To get access to mysql prompt from command line, pass the new socket path with **--sock** option.

> mysql -u root -p **--sock** /opt/lampp/var/mysql/mysql.sock

References: 
[http://dev.mysql.com/doc/refman/5.1/en/problems-with-mysql-sock.html](http://dev.mysql.com/doc/refman/5.1/en/problems-with-mysql-sock.html) 
[http://www.linuxforums.org/forum/red-hat-fedora-linux/92322-phpmyadmin-error-2002-server-not-responding.html#](http://www.linuxforums.org/forum/red-hat-fedora-linux/92322-phpmyadmin-error-2002-server-not-responding.html#)

---

### Post by mistaguy on 2010-09-30
-the problem could that mysql server is not started....you can work around it using the following options:
(1)use
root@wazzabanga:/home/mistaguy# mysqld -u root
the server should start and so u can now access mysql using
root@wazzabanga:/home/mistaguy# mysql u root p
(2)incase this fails; use the option
mysqld --verbose --help
this will give u options that u can use to start the server. u can use the following but its risky in that any one can access your server
root@wazzabanga:/home/mistaguy# mysqld --skip-grant-tables
punch in the following to access the mysql
root@wazzabanga:/home/mistaguy# mysql
once mysql is okay by using any of the options above, u can access phpmysqladmin from your browser as usual provide u provide the okay user details

---

### Post by acompay on 2010-10-23
> **007casper said:**
> just create a mysql user through the terminal and grant all privileges that solves the problem
Please, I have this same problem but do not know how to create a mysqul user and gran all privileges. Where can I find this method? I am using Ubuntu 10.04.
I would appreciate very much your help!
Regards,

---

### Post by tagnu on 2010-10-23
Check this [http://ubuntuforums.org/showthread.php?t=1152326&page=3#21](http://ubuntuforums.org/showthread.php?t=1152326&page=3#21)  > **acompay said:**
> Please, I have this same problem but do not know how to create a mysqul user and gran all privileges. Where can I find this method? I am using Ubuntu 10.04.
I would appreciate very much your help!
Regards,

---

### Post by carsonrose on 2010-10-30
> **ubunter760 said:**
> I found how to correct the problem in case anyone else needs a quick fix:

When recently upgrading my server to Ubuntu 9.04, phpMyAdmin was also upgraded to version 5.0.75. When I loaded up the new version, I was alarmed to find a new error message that read: Connection for controluser as defined in your configuration failed.

It turned out this error was due to the fact that version 5 of phpMyAdmin adds support for a new feature known as a linked-tables infrastructure. This infrastructure allows for new features such as bookmarks, comments, SQL-history, PDF-generation, and field contents transformation. The problem was that this new feature is enabled by default, with generic credentials set up for the controluser. If you don't have your database set up for the infrastructure, you will see the error. I have no use for these new features, so I'd rather just not mess with them. If you do want to enable the advanced features, here is an informative post about doing so on Ubuntu. If you just want to disable the linked-tables infrastructure, which is often the easiest and least intrusive way, just follow these steps:

   1. Type nano /etc/phpmyadmin/config.inc.php in the Linux terminal. You can substitute nano for vi or your favorite text editor.
   2. Find the two blocks of text that read:

      $cfg['Servers'][$i]['controluser'] = $dbuser;
      $cfg['Servers'][$i]['controlpass'] = $dbpass;

      one is near the top embedded in an if statement, and the other is towards the bottom. The text is not exactly the same for each block, but $cfg['Servers'][$i]['controluser'] is what matters. The block that is actually used by phpMyAdmin depends on your setup, but just for simplicity we will apply the change to both.
   3. Just comment out those four lines by adding a // in front of each one.
   4. Save, and the error should disappear next time you access phpMyAdmin. If you are still having trouble, feel free to post a comment.
Worked for me!

---

### Post by dysentry on 2011-01-28
Another reaon you can get this problem is when the phpmyadmin database has not been configured properly, in my instance my database was stored on a remote cluster, so when phpmyadmin installed it called dbconfig-common which failed because the user I entered did not have the correct permissions dbconfig-common is the package which phpmyadmin uses to setup the pma (phpmyadmin database)

So solve the problem for me:
Created phpmyadmin user for any host:
mysql> create user 'phpmyadmin'@'%' identified by 'password';
mysql> grant all privileges on *.* to 'phpmyadmin'@'%' with grant option;

(Previously it was restricted to localhost only).  Remember mysql lets you define an account by a username AND a hostname.  So the same username can exist for multiple hosts.  The key thing here is the % which says "any host".

Then can either run:
# dpkg-reconfigure dbconfig-common
OR manually edit:
/etc/phpmyadmin/config-db.php
Make sure the details are correct.

Then since dbconfig-common had trouble creating the pmadb, we need to generate this database and its tables.  The sql to do this is stored in create_tables.sql.  Lets find it:
# updatedb
# locate create_tables.sql
/usr/share/doc/phpmyadmin/examples/create_tables.sql.gz
The file might be zipped, mine is.
# cd /usr/share/doc/phpmyadmin/examples
# gunzip create_tables.sql.gz

Create the database and tables by importing the sql:
# mysql -u root -p -h myhostname < create_tables.sql

Solved.

Hope that helps.

On a side note, it is "best" NOT to edit /etc/phpmyadmin/config.inc.php (in the four places) and do the hack of entering in a user and password, but instead edit /etc/phpmyadmin/config-db.php and simply put your username and password in there.  The reason being is the config.inc.php gets the variable $dbpass and $dbuser unchain FROM config-db.php.  By editing the lower level file config.inc.php by hand you can cause problems when updating phpmyadmin in the future and simply keep on reintroducing the problem depending on how you update.  The problem that appears to cause this is the dbconfig-common package did not correctly create this file (either through user error, a bug on dbconfig-common, or a problem with phpmyadmins use of cbconfig-common).

---

### Post by fiddyp on 2011-03-01
for me it happened because I changed the IP of my Ubuntu VM when I moved to a new router.

simple fix was to edit [COLOR="Red"]/etc/mysql/my.cnf[/COLOR] and change the IP of the bind-address to the new IP

(also do a [COLOR="red"]sudo restart mysql[/COLOR] afterwards)

thank you internets for providing the answer!

---

### Post by decodejunky on 2011-08-12
Thnx dude!

---

### Post by praveenksubedar on 2011-09-24
> **ubunter760 said:**
> I found how to correct the problem in case anyone else needs a quick fix:

When recently upgrading my server to Ubuntu 9.04, phpMyAdmin was also upgraded to version 5.0.75. When I loaded up the new version, I was alarmed to find a new error message that read: Connection for controluser as defined in your configuration failed.

It turned out this error was due to the fact that version 5 of phpMyAdmin adds support for a new feature known as a linked-tables infrastructure. This infrastructure allows for new features such as bookmarks, comments, SQL-history, PDF-generation, and field contents transformation. The problem was that this new feature is enabled by default, with generic credentials set up for the controluser. If you don't have your database set up for the infrastructure, you will see the error. I have no use for these new features, so I'd rather just not mess with them. If you do want to enable the advanced features, here is an informative post about doing so on Ubuntu. If you just want to disable the linked-tables infrastructure, which is often the easiest and least intrusive way, just follow these steps:

   1. Type nano /etc/phpmyadmin/config.inc.php in the Linux terminal. You can substitute nano for vi or your favorite text editor.
   2. Find the two blocks of text that read:

      $cfg['Servers'][$i]['controluser'] = $dbuser;
      $cfg['Servers'][$i]['controlpass'] = $dbpass;

      one is near the top embedded in an if statement, and the other is towards the bottom. The text is not exactly the same for each block, but $cfg['Servers'][$i]['controluser'] is what matters. The block that is actually used by phpMyAdmin depends on your setup, but just for simplicity we will apply the change to both.
   3. Just comment out those four lines by adding a // in front of each one.
   4. Save, and the error should disappear next time you access phpMyAdmin. If you are still having trouble, feel free to post a comment.


i have tried as u said error has gone but unable to login with my password ..... what should i do next plz help me

---

### Post by rvdavid on 2011-12-16
Hi Praveenksubedar, 

> **praveenksubedar said:**
> i have tried as u said error has gone but unable to login with my password ..... what should i do next plz help me

Try and follow the instructions on the following link - it seems to have helped others with a similar problem. 

[http://www.rvdavid.net/how-to-fix-phpmyadmin-error-connection-for-controluser-as-defined-in-your-configuration-failed/](http://www.rvdavid.net/how-to-fix-phpmyadmin-error-connection-for-controluser-as-defined-in-your-configuration-failed/)

Let me know how you go with it. 

HTH. 

regards,

RV David

---

### Post by farismuttaqin on 2012-03-13
Thanx Thats Works Fine For Me Too

Regards, ):P

---

### Post by phpmysql on 2013-02-26
> **ubunter760 said:**
> I found how to correct the problem in case anyone else needs a quick fix:

When recently upgrading my server to Ubuntu 9.04, phpMyAdmin was also upgraded to version 5.0.75. When I loaded up the new version, I was alarmed to find a new error message that read: Connection for controluser as defined in your configuration failed.

It turned out this error was due to the fact that version 5 of phpMyAdmin adds support for a new feature known as a linked-tables infrastructure. This infrastructure allows for new features such as bookmarks, comments, SQL-history, PDF-generation, and field contents transformation. The problem was that this new feature is enabled by default, with generic credentials set up for the controluser. If you don't have your database set up for the infrastructure, you will see the error. I have no use for these new features, so I'd rather just not mess with them. If you do want to enable the advanced features, here is an informative post about doing so on Ubuntu. If you just want to disable the linked-tables infrastructure, which is often the easiest and least intrusive way, just follow these steps:

   1. Type nano /etc/phpmyadmin/config.inc.php in the Linux terminal. You can substitute nano for vi or your favorite text editor.
   2. Find the two blocks of text that read:

      $cfg['Servers'][$i]['controluser'] = $dbuser;
      $cfg['Servers'][$i]['controlpass'] = $dbpass;

      one is near the top embedded in an if statement, and the other is towards the bottom. The text is not exactly the same for each block, but $cfg['Servers'][$i]['controluser'] is what matters. The block that is actually used by phpMyAdmin depends on your setup, but just for simplicity we will apply the change to both.
   3. Just comment out those four lines by adding a // in front of each one.
   4. Save, and the error should disappear next time you access phpMyAdmin. If you are still having trouble, feel free to post a comment.

Thank you very very much. It solved my problem. I became a member only that can thank you for this post! :);)

---

### Post by oldos2er on 2013-02-26
Old thread closed, please don't bump old threads.

---

