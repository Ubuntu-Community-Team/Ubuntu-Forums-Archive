---
title: "Embarrassing newbie question"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by DanCP on 2010-10-25
So, I installed Zoneminder surveillance software using the Ubuntu software center. Typically when I install stuff, it appears in the "Applications" section - Zonemiinder does not. How can I launch it?

---

### Post by Quackers on 2010-10-25
Some Linux programmes don't have a GUI. I don't know about Zoneminder though.
If you open up a terminal (Applications > Accessories > terminal) and type in zoneminder and press enter it should run.

---

### Post by ArgusVision on 2010-10-25
Zoneminder is acessed through your web browser. I dont recall the port number. Check the website for instructions.

[www.zoneminder.com](www.zoneminder.com)

---

### Post by ArgusVision on 2010-10-25
General Wiki - [http://www.zoneminder.com/wiki/index.php/Contents](http://www.zoneminder.com/wiki/index.php/Contents)

Main Documentation Wiki - [http://www.zoneminder.com/wiki/index.php/Main_Documentation](http://www.zoneminder.com/wiki/index.php/Main_Documentation)

---

### Post by DanCP on 2010-10-25
Thank you. I am making progress, but I'm getting stuck on one step[COLOR=Red] (in red below)[/COLOR]:

When I enter that command, I get a SQL syntax error. What am I doing wrong?
** Installing Zoneminder **

 This is dead easy.  I'll post a shell script to do this soon.  Stuff in **bold** means enter it at the command line and then press ENTER. 
 
[LIST=1]
[*] open a terminal window (Applications > Accessories > Terminal)
[*] $ **sudo apt-get install zoneminder**
[*] $ **sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf**
[*] $ **sudo /etc/init.d/apache2 force-reload** (restarts Apache)
[*] $ **sudo mysql -u root -p < /usr/share/zoneminder/db/zm_create.sql**
[*] **mysql -u root -p** (this brings you into a mysql shell)
[*] [COLOR=Red]> **grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';**[/COLOR]
[*] > **flush privileges;**
[*] > **quit** (this exits the mysql shell)
[*] $ **sudo chmod 4755 /usr/bin/zmfix**
[*] $ **zmfix -a**
[*] $ **sudo adduser www-data video**
[*] $ **sudo gedit /etc/sysctl.conf** (this launches gedit)
[*] scroll to the bottom of the file and paste in the following: *kernel.shmall = 134217728 kernel.shmmax = 134217728*  (Note: This only takes effect after a reboot)
[*] To increase the shared memory on a live system;
[*] $ echo 134217728 >/proc/sys/kernel/shmall
[*] $ echo 134217728 >/proc/sys/kernel/shmmax
[*] save the file (File > Save or CTRL+S)
[*] exit gedit
[/LIST]

---

### Post by krishnandu.sarkar on 2010-10-25
> **DanCP said:**
> 
[LIST=1]
[*] [COLOR=Red]> **grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';**[/COLOR]
[/LIST]


Well..that means create a user named "zmuser" with password "zmpass".
Now create a database zm
Now give the user "zmuser" those (select, insert, update, delete) privileges on zm database.

---

### Post by SeijiSensei on 2010-10-25
Try putting localhost in single quotes as well:

```
grant select,insert,update,delete on zm.* to 'zmuser'@'localhost' identified by 'zmpass';
```

I'm pretty sure that will solve it, but here's the MySQL documentation for the GRANT command should you need it: [http://dev.mysql.com/doc/refman/5.0/en/grant.html](http://dev.mysql.com/doc/refman/5.0/en/grant.html)

---

### Post by DanCP on 2010-10-25
> **SeijiSensei said:**
> Try putting localhost in single quotes as well:

```
grant select,insert,update,delete on zm.* to 'zmuser'@'localhost' identified by 'zmpass';
```I'm pretty sure that will solve it, but here's the MySQL documentation for the GRANT command should you need it: [http://dev.mysql.com/doc/refman/5.0/en/grant.html](http://dev.mysql.com/doc/refman/5.0/en/grant.html)


mysql> grant select,insert,update,delete on zm.* to 'zmuser'@'localhost' indentified by 'zmpass';

ERROR  1064 (42000): You have an error in your SQL syntax; check the manual  that corresponds to your MySQL server version for the right syntax to  use near 'indentified by 'zmpass'' at line 1

---

### Post by realzippy on 2010-10-25
edit.
should have read thread correctly.sorry.

---

### Post by ArgusVision on 2010-10-25
Did you create the zmuser as suggested earlier? I'm not a database/guy but I don't think you need the apostrophes around localhost... no offense intended toward SeijiSensei's suggestion. 
It's been at least a year since the last time I used Zoneminder, but I don't remember having to do that. Just had to create zmuser... actually I might have just given access to an existing user...?  Like I said, it's been a while.

---

### Post by SeijiSensei on 2010-10-26
> **DanCP said:**
> mysql> grant select,insert,update,delete on zm.* to 'zmuser'@'localhost' indentified by 'zmpass';

ERROR  1064 (42000): You have an error in your SQL syntax; check the manual  that corresponds to your MySQL server version for the right syntax to  use near 'indentified by 'zmpass'' at line 1

You misspelled "identified" as "indentified"!  Sometimes the simplest errors are the hardest to find!

---

### Post by realzippy on 2010-10-26
> **SeijiSensei said:**
> You misspelled "identified" as "indentified"!  Sometimes the simplest errors are the hardest to find!

You mean identified as ident[COLOR="Red"]e[/COLOR]fied?  :)   
So this should be it:
```
grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';
```

---

### Post by SeijiSensei on 2010-10-27
Or 'localhost'.

---

