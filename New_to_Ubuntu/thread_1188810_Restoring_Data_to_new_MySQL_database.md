---
title: "Restoring Data to new MySQL database"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by jasonbrisbane on 2009-06-16
Hello All,

I've been maintaining a database for my wiki site on my UBunut server running LAMP. I've got PhpMyAdmin, MySql and php (obviously) and can backup the data to a textfile database which I can be saved on other machines, so it seems that PhpMyAdmin works wonderfully for that purpose..

My issue and question is this:
I have had issues trying to restore data after a complete server failure (Hard drive died and couldnt be restored) where I re-installed the same Ubuntu on a different mahcine whcih became the new server. Everything worked (including Apache, etc), but I couldnt restore the database (I was manually restoring, not using phpMyAdmin).

Is phpMyAdmin the best option to attempt to restore an entire database (or multiple databases) back onto the server again?

How have others restored Mysql data after a complete database/server failure?

Thanks in advance,
A self taught admin... :oops:

---

### Post by theDaveTheRave on 2009-06-16
JasonBrisbane

it depends on how you have exported the data?

I don't know how you would do this from php myqdmin, unless you have access to the mysqldump? otherwise I'm affraid that you will need to be using the command line.

NOTE, *_you don't need to log in to the server_*, you need to run this directly from the cli, 

```

mysqldump -u [COLOR="Red"]yourUserName[/COLOR] -p --a all-databases > /tmp/my[COLOR="Red"]WholeDatabase[/COLOR].sql

```

Obvously this will need to be done from the command line, edit in your mysql username to replace <[COLOR="Red"]yourUserName[/COLOR]>, and change <[COLOR="Red"]myWholeDatabase[/COLOR]> to a file name of your choice (but don't change the extension as this will tell the server you are using a file that contains mysql script code. You will be asked for your password once you have hit the enter key.

You need to put this into the /tmp/ folder otherwise there are permission issues with read / write, so this makes it nice and easy.

then to restore the data back into a new database, copy the file to the new system again put it in /tmp for ease of read / write access.

then use this code...
```

mysql -u [COLOR="Red"]yourUserame[/COLOR] -p </tmp/[COLOR="Red"]myWholeDatabase[/COLOR].sql

```

That should copy *_everything_*, including your usernames and passwords, so on the new server you will be able to start using your  usernames . passwords from the old server without any issue...

BUT - you will need to create a new user / password combination (with admin privileges) on the new server to enable you to run this command.

Check that the structure is good, and then keep a copy of that dump file for emergency backup should you have a problem in the future.

Hope that gets you going.

Here is the link to the page on the mysql site for [using mysqldump]("http://dev.mysql.com/doc/refman/6.0/en/replication-howto-mysqldump.html")

it can make for rather heavy reading... but it is a very complete reference, check it out.

---

### Post by indytim on 2009-06-16
phpMyAdmin works very well for restoring tables within a database.  The limitation may be on a very large table that will exceed the limits established by your php.ini file.  Otherwise, do an export from your existing MySQL database to a sql file.  On the flip side, AFTER you have created the database in your new server, Select the import tab on phpMyAdmin and you should be good-to-go.  Remember on the export side to also export the structure.  One final cavaet, if you are using InnoDB, with foreign keys setup, you will have to be careful about the order that you reload your database.

Hope this helps.

-DataMan

---

### Post by ActiveFrost on 2009-06-16
I would suggest you to install *mysql-admin* and restore your database from there. phpMyAdmin is good only if you need to create/delete/populate databases, not to restore/backup them ;)

---

### Post by s.fox on 2009-06-16
Hi,

How did you export the data? What format? 

-Ash R

---

### Post by indytim on 2009-06-16
> phpMyAdmin is good only if you need to create/delete/populate databases, not to restore/backup them 

Wrong!  You can easily do a restore within phpMyAdmin.  I do it on a regular basis in a development environment.

IndyTim

---

### Post by ActiveFrost on 2009-06-16
> **indytim said:**
> Wrong!  You can easily do a restore within phpMyAdmin.  I do it on a regular basis in a development environment.

IndyTim

Actually, it's not wrong ! Both options will do the job - it's all about the taste and experience. This is a place where you ask and get 10 different answers, right ? So, my answer is my experience and taste - that's all ;)

---

