---
title: "Installed Drupal6 - where is it?"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by LearningPerson on 2011-03-14
Hello,  I just upgraded to Lucid Lynx and want to use Drupal6x.  I "installed" it under the Synaptic Package Manager but now can't find it!  Tried the terminal, Find and Show Hidden Files.  

Any ideas?

Thanks, Sharon

---

### Post by stoogiebuncho on 2011-03-14
Did you try typing 'locate drupal' in a terminal?

If that doesn't work, I can check when I get home.  I don't remember off the top of my head where it saved the files on my machine.

---

### Post by LearningPerson on 2011-03-14
Thanks, Stoogiebuncho.  Yes, I did do that and absolutely nothing comes back....it's as though I just opened the terminal.  I'll remove and try to re-install but any other help would be great.  I expected to see an icon or a page open or ???

Sharon

---

### Post by QLee on 2011-03-14
Since you're using Synaptic, select the package name and then Package-->Properties, the property sheet has an Installed Files tab that shows the location of the files the package manager installed.

---

### Post by LearningPerson on 2011-03-14
Hi GLee,

Just did that and several files are listed.  When I go to the terminal and type in "locate -----" for several files and nothing shows up!

I'm wondering: although the installation process says to Close I can still see the circle rotating.  Is this a problem?

Also, with the first installation, I didn't put in any passwords; just pressed Forward.  Then I Removed and did another installation....which was suspicioulsy FAST.

Any ideas?    OH, Could I do a sudo apt-get drupal6 from the terminal?  Well, maybe Remove first?

Sharon

---

### Post by stoogiebuncho on 2011-03-14
My files are in /usr/share/Drupal6/

If yours aren't there you might consider doing a complete removal (right-click in synaptic and mark for complete removal or apt-get purge in the terminal) and reinstall.  Take your time going through the setup questions to make sure everything is correct.

---

### Post by LearningPerson on 2011-03-14
Here's what I got when I went to the terminal and did "Sudo get-apt install Drupal6":      An error occurred while installing the database.    ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using      &#9474; 
 &#9474; password: YES)  

Do you know what that means?

Sharon

---

### Post by stoogiebuncho on 2011-03-14
Did you do the purge removal thing before reinstalling?

---

### Post by LearningPerson on 2011-03-14
Yes, I did.  

When I went to reinstall which again didn't take, here is what the terminal reads:
```
sharon@sharon-desktop:~$ sudo apt-get install drupal6

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  libhpricot-ruby1.8 libcommandline-ruby java-common google-chrome-beta

  odbcinst libruby unixodbc ruby1.8 sdparm ruby odbcinst1debian1

  libcommandline-ruby1.8 libhpricot-ruby libruby1.8 libtext-format-ruby1.8

  libopen4-ruby1.8

Use 'apt-get autoremove' to remove them.

The following NEW packages will be installed:

  drupal6

0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B/1,115kB of archives.

After this operation, 5,067kB of additional disk space will be used.

Selecting previously deselected package drupal6.

(Reading database ... 162386 files and directories currently installed.)

Unpacking drupal6 (from .../drupal6_6.16-1ubuntu0.1_all.deb) ...

Setting up drupal6 (6.16-1ubuntu0.1) ...

dbconfig-common: writing config to /etc/dbconfig-common/drupal6.conf



Creating config file /etc/dbconfig-common/drupal6.conf with new version



Creating config file /etc/drupal/6/sites/default/dbconfig.php with new version

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).

unable to connect to mysql server.

error encountered creating user:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

dbconfig-common: drupal6 configure: trying again.

dbconfig-common: writing config to /etc/dbconfig-common/drupal6.conf

Replacing config file /etc/drupal/6/sites/default/dbconfig.php with new version

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).

unable to connect to mysql server.

error encountered creating user:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

dbconfig-common: drupal6 configure: trying again (skip questions).

dbconfig-common: writing config to /etc/dbconfig-common/drupal6.conf

Replacing config file /etc/drupal/6/sites/default/dbconfig.php with new version

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).

unable to connect to mysql server.

error encountered creating user:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

dbconfig-common: drupal6 configure: ignoring errors from here forwards

dbconfig-common: flushing administrative password

dbconfig-common: drupal6 configure: ignoring errors from here forwards

dbconfig-common: drupal6 configure: ignoring errors from here forwards

www-data www-data 750 /var/lib/drupal6/files



Can you see what I did wrong?
```

Sharon

---

### Post by LearningPerson on 2011-03-14
Hello again,  

The problem seems to be the dbconfig-common file but I have no clue what to do with it.

S

---

### Post by stoogiebuncho on 2011-03-14
Does it still ask you for your password when you try to install Drupal?

Here's my guess on what's going on:

You installed MySQL at some point, either before drupal, or the first time you installed drupal.  You set up a password for it (or maybe you skipped that?)

The first time you installed drupal it asked for your mysql password, and you skipped that page.  So now it's giving you an error because you don't have the correct password for mysql.

Here are ideas to try (I haven't tried any of these things before):

1) Purge drupal again.  See if the dbconfig-common file is still there.  If it is, delete it (you could even delete the whole drupal).  Reinstall drupal.  

OR

2) Purge drupal AND mysql.  Reinstall.

---

### Post by LearningPerson on 2011-03-14
Hi Stoogiebuncho,

Here is the latest which looks as though all is fine....however, I see no icon for Drupal6 and cannot "locate" in through the terminal.  I must be doing something wrong that is very simple.

```
sharon@sharon-desktop:~$ sudo apt-get install drupal6

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  libhpricot-ruby1.8 libcommandline-ruby java-common google-chrome-beta

  odbcinst libruby unixodbc ruby1.8 sdparm ruby odbcinst1debian1

  libcommandline-ruby1.8 libhpricot-ruby libruby1.8 libtext-format-ruby1.8

  libopen4-ruby1.8

Use 'apt-get autoremove' to remove them.

The following NEW packages will be installed:

  drupal6

0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B/1,115kB of archives.

After this operation, 5,067kB of additional disk space will be used.

Selecting previously deselected package drupal6.

(Reading database ... 162386 files and directories currently installed.)

Unpacking drupal6 (from .../drupal6_6.16-1ubuntu0.1_all.deb) ...

Setting up drupal6 (6.16-1ubuntu0.1) ...

dbconfig-common: writing config to /etc/dbconfig-common/drupal6.conf



Creating config file /etc/dbconfig-common/drupal6.conf with new version



Creating config file /etc/drupal/6/sites/default/dbconfig.php with new version

granting access to database drupal6 for drupal6@localhost: already exists.

creating database drupal6: success.

verifying database drupal6 exists: success.

dbconfig-common: flushing administrative password

www-data www-data 750 /var/lib/drupal6/files
```

---

### Post by stoogiebuncho on 2011-03-14
Sounds like it's probably working.  I forgot that "locate" works off of an index, so it probably won't return any results until the index is updated.

Drupal doesn't have an icon anywhere, you just point your web browser to it.  I think the default location is [http://localhost/drupal/]("http://localhost/drupal/")

Try that out and see what it does.

---

### Post by LearningPerson on 2011-03-14
Um, I don't know HOW to point my browser at [http://localhost/drupal/](http://localhost/drupal/)    When I entered the URL, I got:  Not Found

The requested URL /drupal/ was not found on this server.
Apache/2.2.14 (Ubuntu) Server at localhost Port 80

Any help....Sharon

---

### Post by stoogiebuncho on 2011-03-14
Ok, two questions:

Open up a file manager.   Go to /var/www/.  Is there anything there?

Now go to /usr/share/.  Can you find a drupal6 folder?

---

### Post by LearningPerson on 2011-03-14
I went into Places, Find and entered the two names you listed.  Nothing.  Then I went into the terminal and wrote:   find /var/www/  I got:  /var/www/
/var/www/index.html

When I wrote find /usr/share/  I found: /usr/share/lintian/overrides/drupal6


Yet Synaptic says it is installed!

---

### Post by stoogiebuncho on 2011-03-14
Ok, open a terminal and paste this in:

```
sudo ln -s /usr/share/drupal6/ /var/www/
```

Assuming both directories exist, this will create a soft link to your drupal folder from your www folder.  If they don't both exist, it will give you an error message.  Post the error if you get one.


If no errors, open up a web browser, go to the url bar, and enter [http://localhost/drupal/](http://localhost/drupal/)

---

### Post by LearningPerson on 2011-03-14
Thanks for sticking with this!

Nothing.  Here are the results:
sharon@sharon-desktop:~$ sudo ln -s /usr/share/drupal6/ /var/www/
[sudo] password for sharon: 
sharon@sharon-desktop:~$

---

### Post by LearningPerson on 2011-03-14
OMG, Stoogiebuncho,  I got out of the terminal then went back in and saw:

sharon@sharon-desktop:~$ sudo ln -s /usr/share/drupal6/ /var/www/
ln: creating symbolic link `/var/www/drupal6': File exists

However, [http://localhost/drupal/](http://localhost/drupal/) doesn't work.   Can I somehow do it from the terminal?  Or what are the exact steps?

---

### Post by LearningPerson on 2011-03-14
OMG again!  I added to your URL: [http://localhost/drupal6/](http://localhost/drupal6/) and Drupal came up.  Sort of.  It says:
Site off-line

The site is currently not available due to technical problems. Please try again later. Thank you for your understanding.

If you are the maintainer of this site, please check your database settings in the settings.php file and ensure that your hosting provider's database server is running. For more help, see the handbook, or contact your hosting provider.
 
Now what?

---

### Post by stoogiebuncho on 2011-03-14
It sounds like drupal is not communicating with your mysql database.  This is probably because something wasn't installed properly, or you entered a wrong password (or left the password field blank) when you installed.

Put this in a terminal:
```
gksudo gedit /etc/drupal/6/sites/default/dbconfig.php 

```

That will open your database config file.  This is what mine looks like (with the password taken out, of course).
```
<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/drupal6.conf
## by /usr/sbin/dbconfig-generate-include
## Thu, 10 Feb 2011 17:29:41 -0600
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='drupal6';
$dbpass='****************';
$basepath='';
$dbname='drupal6';
$dbserver='';
$dbport='';
$dbtype='mysql';
```

Does yours look similar to that?

---

### Post by LearningPerson on 2011-03-14
Here it is:

<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/drupal6.conf
## by /usr/sbin/dbconfig-generate-include
## Mon, 14 Mar 2011 15:30:06 -0700
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='drupal6';
$dbpass='******';
$basepath='';
$dbname='drupal6';
$dbserver='';
$dbport='';
$dbtype='mysql';

---

### Post by stoogiebuncho on 2011-03-14
Ok, let's see if we can narrow this down a little bit more.

Go back to the terminal - we're going to try to log into mysql using the information that drupal has saved.  Type this in:
```
mysql -u drupal6 -p

```
When it asks you for a password, enter the password you found in your dbconfig.php file.

If it works, you'll see something like this:
mysql>

You can just type 'exit' to get out of it.

If it doesn't work, you'll get an error, and hopefully it will tell us something helpful.

---

### Post by LearningPerson on 2011-03-14
I entred the password from "dbpass" and received this:

sharon@sharon-desktop:~$ mysql -u drupal6 -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'drupal6'@'localhost' (using password: YES)
sharon@sharon-desktop:~$ 
  
Doesn't look so good.

---

### Post by LearningPerson on 2011-03-14
Oh.  I entered my terminal password and got this:

sharon@sharon-desktop:~$ mysql -u drupal6 -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 62
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

---

### Post by LearningPerson on 2011-03-14
Oops.  The terminal message ended with:   mysql>

---

### Post by LearningPerson on 2011-03-14
Yes, here is a problem:  The dbpass is one word.  The terminal password has one addl letter.  

The dbpass password returns an error.

The terminal password does not. 

How can I get rid of the dbpass password?  If that is the answer?

---

### Post by stoogiebuncho on 2011-03-14
Ok, I think we're getting somewhere.  It looks like the drupal password was not set correctly.

Good news, we should be able to fix this!

First, you need to log into mysql again, but this time, as root:
```
mysql -u root -p
```
Enter your normal password here.

You should see the 'mysql>' again.

Next, select the mysql database:
```
use mysql;
```

Now change the password to the password that is in your dbconfig file
```
update user set password=PASSWORD("DBCONFIG-PASSWORD-HERE") where User='drupal6';
```

After that, go back to [http://localhost/drupal6/](http://localhost/drupal6/) and see if it works.

---

### Post by LearningPerson on 2011-03-14
Oh horsefeathers!  When I enter either my sudo terminal password or the dbpass password, I get:  

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by LearningPerson on 2011-03-14
Aha!  When I enter nothing, I get    mysql>    again.  Shall I go ahead now?    But what do I use the dbpass password for?

---

### Post by stoogiebuncho on 2011-03-14
> **LearningPerson said:**
> Aha!  When I enter nothing, I get    mysql>    again.  Shall I go ahead now?    But what do I use the dbpass password for?

Ok, that means that you never set a root password for mysql.  If you are hosting an actual website that's online, this is a big security problem.  If you're only playing with drupal on your own machine (and no one else can access the site), it doesn't really matter.

Assuming this is only on your machine, it's ok to proceed with the other commands to change the password for drupal6.

---

### Post by LearningPerson on 2011-03-14
Is it the terminal (sudo) password I want from the dbconfig file or the Drupal dbpass password.

When you tell me which one, do I write:

pdate user set password=**** where User='drupal6'

without any semi-colon at the end and with the exact spacing as above?

---

### Post by LearningPerson on 2011-03-14
This is just for playing.  Later someone else will put in their password.

But I'm still confused about which password to use?

---

### Post by stoogiebuncho on 2011-03-14
Ok, let's do this step by step again.

The password you want is the one in your dbconfig file:
```
<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/drupal6.conf
## by /usr/sbin/dbconfig-generate-include
## Mon, 14 Mar 2011 15:30:06 -0700
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded. *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='drupal6';
$dbpass='******';
$basepath='';
$dbname='drupal6';
$dbserver='';
$dbport='';
$dbtype='mysql';
```

It's the one that you hid with the asterisks. 

So go to a terminal:
1.
```
mysql -u root -p
```
leave the password blank and press enter.  Now you should see the mysql>

2.```
use mysql;
```

3.```
update user set password=PASSWORD("**********") where User='drupal6';
```
You need ALL of that - just copy and paste it into the terminal, and then change the asterisks to the password.  Leave in the PASSWORD("") part, and leave in the ; at the end.

4. (I forgot you need to do this to make the changes take effect)
```
FLUSH PRIVILEGES;
```

5. Exit mysql:
```
exit
```

6. Go to [http://localhost/drupal6/](http://localhost/drupal6/)

---

### Post by LearningPerson on 2011-03-14
Here is what I got:

sharon@sharon-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 85
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> update user set password=PASSWORD("civil") where User='drupal6';
ERROR 1046 (3D000): No database selected

---

### Post by stoogiebuncho on 2011-03-14
You have to do the ```
use mysql; 
``` command before you can enter the command to change the password.

---

### Post by LearningPerson on 2011-03-14
This is what I did this time:

sharon@sharon-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 90
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update user set password=PASSWORD("civil") where User='drupal6';
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> exit

---

### Post by LearningPerson on 2011-03-14
Ooops.  And the result of pasting in the URL of:  [http://localhost/drupal6/](http://localhost/drupal6/)     was a blank page.

---

### Post by stoogiebuncho on 2011-03-14
Well, drupal is connecting to the database, so that's good, but it looks like there's some other problem.

I don't know that I have time to diagnose anything else tonight - I'd suggest looking through this and seeing if anything helps your situation. 
[http://drupal.org/node/158043]("http://drupal.org/node/158043")

If you can turn on error reporting it would probably help you a lot, and you could post the errors back here.

---

### Post by LearningPerson on 2011-03-14
Thanks so much for your help!  And I'll do that.

---

### Post by stoogiebuncho on 2011-03-16
To turn on error reporting:

```
gksudo gedit /usr/share/drupal6/index.php
```

The beginning of the file should look something like this:
```
<?php
// $Id: index.php,v 1.94 2007/12/26 08:46:48 dries Exp $

/**
 * @file
 * The PHP page that serves all page requests on a Drupal installation.
```

In between this line:
```
<?php
```
and this line:
```
// $Id: index.php,v 1.94 2007/12/26 08:46:48 dries Exp $
```

paste this code:
```
error_reporting(E_ALL);
ini_set('display_errors', TRUE);
ini_set('display_startup_errors', TRUE);
```

Then go back to your drupal page and see what it says.

---

### Post by LearningPerson on 2011-03-16
Will keep the above instruction but meanwhile here's what I did, Stoogie:

I think phpMyAdmin needs to be installed first.  After messing both programs up again I removed Drupal6 (no deconfig of db here; there wasn't one) and then removed phpAdmin.  I reinstalled both with NO passwords.  Can be done later.
Was able to bring up phpMyAdmin at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and Drupal6 says I am Forbidden. Think this is good news as I must have to go into phpMyAdmin first and set that up.
Since I am just playing with this, can I go into phpMyAdmin and have the Username of 'root' and no password?
Then maybe go back into [http://localhost/drupal6/?](http://localhost/drupal6/?) With 'root' as the dbuser this time and no password?
Sharon

---

### Post by stoogiebuncho on 2011-03-16
You don't need phpmyadmin.  It doesn't hurt, but it doesn't allow you to do anything that you couldn't do before.  It's just a graphical way of dealing with mysql.

The username for drupal NEEDS to be drupal6, and the password NEEDS to be the password we found in the dbconfig file (I believe it was 'civil').  Changing these to root and blank will not fix your problem. 

Change the drupal6 password back to civil (either using phpMyAdmin or the instructions I gave before), then enable error reporting and see what your drupal page says then.

---

### Post by LearningPerson on 2011-03-16
Ok, stoogie, I did that.  Then went to the Drupal6 page which returned:
Warning: Table 'drupal6.access' doesn't exist query: SELECT 1 FROM access WHERE type = 'host' AND LOWER('127.0.0.1') LIKE LOWER(mask) AND status = 0 LIMIT 0, 1 in /usr/share/drupal6/includes/database.mysql.inc on line 128 Warning: Table 'drupal6.users' doesn't exist query: SELECT u.*, s.* FROM users u INNER JOIN sessions s ON u.uid = s.uid WHERE s.sid = 'oljd1ilma1h94earrdqnj8ash0' in /usr/share/drupal6/includes/database.mysql.inc on line 128 Warning: Table 'drupal6.cache' doesn't exist query: SELECT data, created, headers, expire, serialized FROM cache WHERE cid = 'variables' in /usr/share/drupal6/includes/database.mysql.inc on line 128 Warning: Table 'drupal6.variable' doesn't exist query: SELECT * FROM variable in /usr/share/drupal6/includes/database.mysql.inc on line 128 Notice: Undefined variable: variables in /usr/share/drupal6/includes/bootstrap.inc on line 480 Warning: Table 'drupal6.cache' doesn't exist query: UPDATE cache SET data = '', created = 1300313287, expire = 0, headers = '', serialized = 0 WHERE cid = 'variables' in /usr/share/drupal6/includes/database.mysql.inc on line 128 Notice: Undefined variable: variables in /usr/share/drupal6/includes/bootstrap.inc on line 487 Warning: Table 'drupal6.system' doesn't exist query: SELECT name, filename, throttle FROM system WHERE type = 'module' AND status = 1 AND bootstrap = 1 ORDER BY weight ASC, filename ASC in /usr/share/drupal6/includes/database.mysql.inc on line 128 Warning: Table 'drupal6.url_alias' doesn't exist query: SELECT COUNT(pid) FROM url_alias in /usr/share/drupal6/includes/database.mysql.inc on line 128 

Can you figure that?

Sharon

---

### Post by gsocker on 2011-03-16
Just installed a fresh copy of 10.10 in the virtual machine, then installed drupal. After some banging, I got it working.

Two things: 
Drupal needs to be initially configured. To do this:
visit [http://localhost/drupal6/install.php](http://localhost/drupal6/install.php)

If your browser asks you if you want to open or download, please post the contents of /etc/apache2/mods-enabled/php.conf.
Mine had a presupplied error that kept things from working properly.

---

### Post by LearningPerson on 2011-03-16
Hi there,  I don't have a domain?  Do I need to set one up?

Sharon

---

### Post by gsocker on 2011-03-16
Sorry, I'm not sure quite what you mean about the domain name.
Can you be a little more specific?

If you're referring to h ttp://localhost/drupal6/install.php, "localhost" means "on this computer"; it's called the loopback address.

---

### Post by LearningPerson on 2011-03-16
Stoogie,

The site puts in the site name as local host then asks for the site email address?  Sharon

---

### Post by LearningPerson on 2011-03-16
Oh, sorry, I see you're gsocker.  Sharon

---

### Post by LearningPerson on 2011-03-16
gsocker,  Can I just put in one of my email addresses?  Sharon

---

### Post by gsocker on 2011-03-16
For a site you're just playing around with, you can just use root@localhost. Email won't work, but you should be able to try everything else out. If you need the site to be able to send email, then you will need to set it up with a real email address. 

For the moment, I would just use a fake one until you get used to things. Setting up email can be tricky for these types of systems, as most assume that a mail server is running on the same server as the app.

---

### Post by LearningPerson on 2011-03-16
gsocker,  I did enter one of my email addresses and finished the other entries.  I now have a Drupal website!

The only small problem is that emails can't be sent to me evidently from the second line which asked for my site email address.  Will this be a concern?  When this is answered, we can put Solved up there.

Thanks so much!  

Sharon

---

### Post by LearningPerson on 2011-03-16
Oh wow, thanks a bunch, gsocker! Sharon

---

### Post by gsocker on 2011-03-17
Just a follow up to the post about email. Putting a valid address in the field does not in and of itself setup things for email. You must also setup how the system will send email. It appears that the default install does not include support for anything other than a mail server running on the same system. To make it use your ISP's email server, you would need to install the appropriate modules and then configure them. Most webmail services do not provide access via anything other than a web interface, so they would not be usable.

---

