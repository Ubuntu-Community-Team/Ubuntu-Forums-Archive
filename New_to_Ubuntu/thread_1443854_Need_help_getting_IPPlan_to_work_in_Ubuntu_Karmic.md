---
title: "Need help getting IPPlan to work in Ubuntu Karmic"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Bibiwinter on 2010-03-31
Hi,

  Need help!  I'm trying to get IPPlan (Open Source Software to do IP address Management) to work under my installation of Ubuntu Karmik.   I'm not a sysadmin or even power user and the learing curve just to install this seems almost unapproachable as I have no knowledge on Apache.  With my optimism I thought this might be a good occasion to start learning at least how to do a basic setup of Apache, but the more I dig for info, the more I feel like this is too big a monster for my level of knowledge and the time I have, so I just want to back out and I'm looking for a dumb procedure to make IPPlan start.  Unfortunately, there seems to be no such documentation for Ubuntu and IPPlan.  To be honest, this is poorly documented, and most of what exist starts by saying "Once installed and accessible through the Web browser..."   I just want to get there.   The rest, I will manage.  

  I have 2 questions here.  1- With the level of knowledge I have (which you can asses below reading the steps I took so far), is it realistic for me to think that I can get this to work with less than 10-15 hours of reading and scratching my head? and 2- If yes, can someone point me in the right direction as to what exactly I need to read about Apache to at lease start the server for IPPlan.  (And even better, is there some existing good doc about how to set it up in Karmic?)

  Here's what I did so far and here's the problem I face:

  In Synaptic package manager, I selected IPPlan for installation.  It warned me that it will install also Apache2, PHP, MySQL and a list of other apps.   No problem there.   It's all installed.

  Figured out that to access IPPlan, it was through a Web Browser.   Opened up and tested localhost.   Apache works as when I go to [http://127.0.0.1/](http://127.0.0.1/), it tells me  "It worked!".

  Now from the limited doc I could find on the web, it tells I should be able to reach [http://localhost/ipplan](http://localhost/ipplan).  This is where I'm stuck.   Could never get that to work.   Brower tells me page not found.

  Did an "updatedb" then located the ipplan directory in /usr/share/ipplan.   Copied this directory to /etc/apache to make it available in the Apache root (which I found reading  /etc/apache2/apache2.conf), then restarted the service.  Got the error message "Could not reliably determine the server’s fully qualified domain name", which I fixed by adding the line "ServerName localhost" in apache2.conf.  Restarted the service and didn't get the error message anymore.

  Now I'm stuck here.  Just don't know what to do to make Apache serve the IPPlan page.  I think something is missing in Apache to point to the IPPlan directory so it can respond to requests appropriately, but I don't know how to make it happen.  Do you need to write a script or program, or just do some configurations in the .conf files?

  Thanks in advance.

---

### Post by M!K3_$ on 2010-03-31
not sure what you need to do to get IPPlan to work.
but to configure a new page in apache...

i can do that. not from memory though. if you give me a sec i'll bring up my server and then explain.

---

### Post by M!K3_$ on 2010-03-31
ok.

in **/etc/apache2/** you will find two folders.

"sites-enabled" and "sites-available"

What I like to do is go into "sites-available"

```
cd /etc/apache2/sites-available
```

in there there is a default site.

copy the default site and rename it to whatever you want (IPPlan)

```
cp default IPPlan
```
now edit the default config
```
nano IPPlan 
```

it's pretty simple. you should be able to figure out what you need to change just by looking at it.

save you changes. then move your new IPPlan config into the "sites-enabled" folder. i like to delete default in "sites-enabled".

```
mv IPPlan ../sites-enabled/default
```


try that :)

---

### Post by Bibiwinter on 2010-03-31
Hi M!K3_$

  Thanks for the info.  This was more valuable than anything else I found for Apache.  And there seems to be life in there.  Not working yet, and I think I have a priviledge problem but at least I now get a response from the server.

  When I go to:  [http://localhost/ipplan/](http://localhost/ipplan/)
  It tells me:  "Problem with database permission or database tables - have installation instructions been followed?
Could not connect to database"

  And when I go to:  [http://localhost/ipplan/admin/install.php](http://localhost/ipplan/admin/install.php)
  It tells me:  "If you see this message, submit a detailed bug report on Sourceforge including the message below, the database platform used and the steps to perform to recreate the problem.
PHP 5.2.10-2ubuntu6.4 (Linux)
Unknown error type: [2] require_once(/var/www/ipplan/menus/lib/PHPLIB.php) [function.require-once]: failed to open stream: No such file or directory Line: 547 File: /var/www/ipplan/ipplanlib.php

Fatal error: require_once() [function.require]: Failed opening required '/var/www/ipplan/menus/lib/PHPLIB.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/ipplan/ipplanlib.php on line 547"

  ...even though I checked and the files are there. I copied the /ipplan/ directory under /var/www/ and applied the ownership and permissions as defined in Web page [http://openmaniak.com/ipplan_tutorial.php](http://openmaniak.com/ipplan_tutorial.php), but to no avail.

  Thanks again for your help.  Thanks to you I now know a bit more about Apache.  I'll dig further to see if I can fix this permission thing.

---

### Post by M!K3_$ on 2010-03-31
looks like a mysql problem. when you installed IPPlan did it give you some pre-reqs? Looks like you need to make it a database give it proper mysql permissions?

---

### Post by M!K3_$ on 2010-03-31
documentation from their IPPlan

[http://www.openmaniak.com/ipplan.php](http://www.openmaniak.com/ipplan.php)

[http://iptrack.sourceforge.net/documentation/requirements.html](http://iptrack.sourceforge.net/documentation/requirements.html)

[http://iptrack.sourceforge.net/documentation/](http://iptrack.sourceforge.net/documentation/)

---

### Post by M!K3_$ on 2010-03-31
[http://www.openmaniak.com/ipplan_tutorial.php](http://www.openmaniak.com/ipplan_tutorial.php)

look at this. it is good. shows you how to set up your mySQL database, tables and users.

as well as install the rest of the program

---

### Post by Bibiwinter on 2010-03-31
Yep, I also think it's something with MySQL.  All I know is that MySQL  was installed as well as PHP to solve dependencies for IPPlan.  Not sure if this is what you mean by "pre-reqs".

I'm giving up for now on the professional side as I realize we won't be able to support it at the corp level.  We don't have the time/knowledge/long-term resources to debug and maintain the software, in addition to the content of the database.  Back to my Excel spreadsheet. [-(

I'll come back to it very soon at the personal level though, maybe tonight, and see if I figure it out and learn a bit more.

---

### Post by M!K3_$ on 2010-03-31
I work as part of the IT team at a medium size corporation (500 users) and I use a spreadsheet. 

My knowledge of apache/php/mySQL comes from my previous job, supporting a wed developement firm. 

That tutorial looks solid and it comes with screenshots. Dont give up yet. give it a shot.

---

### Post by Bibiwinter on 2010-03-31
[http://www.openmaniak.com/ipplan_tutorial.php](http://www.openmaniak.com/ipplan_tutorial.php)

Yep.  That's the one I was following.  Doesn't do it for me.  Even after following those procedures I get the error messages I listed above.  Tried to do it several times in case I did something wrong the first few times.

Thanks again!

---

### Post by M!K3_$ on 2010-03-31
[https://bugs.launchpad.net/ubuntu/+source/ipplan/+bug/267347](https://bugs.launchpad.net/ubuntu/+source/ipplan/+bug/267347)

This has been reported. But if you read that lunchpad page it's not a bug.

People just arn't reading the readme. 

Check the launchpad page out. it will show you what to do.

---

### Post by Bibiwinter on 2010-03-31
Total newbie situation.  This is way over my head.

Seems like I broke the whole PHP/Apache system.  Out of despair I uninstalled IPPlan and Apache/PHP5 with Synaptics to try to start with fresh files.  Now when I try to reinstall IPPlan, Synaptics gives me an error message saying that the PHP5 module doesn't exist, even if it resolves the dependencies and does reinstall PHP and Apache at the same time.

The error message I get is:

Errors were encountered with processing:
  ipplan
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ipplan (4.91a-1.1)
ERROR: Module php5 does not exist!
dpkg: error processing ipplan (--configure):
 subprocess installed post-installation script returned error exist status 1
Errors were encountered while processing:
 ipplan


I looked for this error and found that thread:  [http://ubuntuforums.org/showthread.php?t=640280](http://ubuntuforums.org/showthread.php?t=640280)

Followed the directives, but didn't help.  Always getting the same error message.  I  tried to reenable the php5 module following the directives in page [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) but it didn't help either.

After uninstalling Apache2 and php, I even deleted the directories /etc/apache2 and /etc/php5 to make sure there were no bad config files left.  Reinstalled ipplan through Synaptic and still same error.

Did I reach the point where I need to reinstall Ubuntu?

As I said, newbie situation...:sad:

---

### Post by Bibiwinter on 2010-03-31
Ok.  Finally managed to reinstall without errors following the directives in the page: 
[http://dancingpenguinsoflight.com/2009/02/how-to-completely-reset-an-apache-instance-in-ubuntu/](http://dancingpenguinsoflight.com/2009/02/how-to-completely-reset-an-apache-instance-in-ubuntu/)

Starting over trying to make sense out of this chaos.

---

### Post by Bibiwinter on 2010-03-31
Now when I restart the apache2 service, I get:

root@Ubuntu:~# server apache2 restart
Starting service Echo...
Echo Server - Version 1.0
=========================

General Parameters:
   Pool Handle             = EchoPool
   Reregistration Interval = 30.000s
   Runtime Limit           = off
   Policy Settings
      Policy Type          = RoundRobin
      Load Degradation     = 0.000%
      Load DPF             = 0.000%
      Weight               = 0
      Weight DPF           = 0.000%
31-Mar-2010 21:09:17.3517: P17235.7f82c88c6710@Ubuntu rserpoolsocket.c:320 doRegistration()
31-Mar-2010 21:09:17.3519: Error: (Re-)Registration failed: no registrar available
Registration
   Identifier              = $00000000



And it hangs there...

I don't see any "echo" service in /etc/init.d

Google doesn't give me any info about an echo service.

---

### Post by M!K3_$ on 2010-03-31
> **Bibiwinter said:**
> Now when I restart the apache2 service, I get:

root@Ubuntu:~# server apache2 restart


You mean:```
service apache2 restart
```


try a reload

```
service apache2 force-reload
```

---

### Post by Bibiwinter on 2010-03-31
Thanks M!K3_$

With your help, I actually managed to get it to work!  At least the login page.  I now know that my Apache2 setup is ok, and so it php5.    Was a mistake in my post above when I wrote "server apache2 restart", but I was doing it right at the shell.

Now moving ahead, I still seem to have something going on with Mysql authentication, though.  When I try to create a new database in the Web page, it prompts me for a username and password, which is normal.  But no matter what I put in, it refuses to let me login.

I ran again through the user account creation process and privilege settings at the mysql prompt, but it still doesn't work.  I just started reading a bit about mysql so barely started working on that.

At this point, I'm wondering if I have to restart something else that apache2 when I modify user accounts in mysql.  But again, there is no mention of that anywhere and there is no mysql or php5 service in /etc/init.d

At least I'm starting to make sense out of all of this.

Thanks!!

---

### Post by Bibiwinter on 2010-03-31
Haven't figured that one out yet.  Tried to create several users at the mysql prompt and no error reported.  Restarted the apache2 service many times, but I still cannot login.

Wondering if I'm missing some package for mysql authentication to work.

Here's a log of what I do:

root@Ubuntu:/etc/ipplan# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 117
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> grant all on ipplan.* to ipplan2@localhost identified by 'ipplan2';
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> create database auth;
Query OK, 1 row affected (0.00 sec)

mysql> exit
Bye
root@Ubuntu:/etc/ipplan# service apache2 restart
 * Restarting web server apache2                                                                                                                              ... waiting                                                                                                                                          [ OK ]
root@Ubuntu:/etc/ipplan#

My brain is fried. fnord

---

### Post by M!K3_$ on 2010-03-31
You dont need to restart apache2 when you make changes to your database (or users).
Think about it; if everytime a database changed you had to restart apache. You wouldn't have a very functional webpage.

Make sure that IPPlan wants to use the same username/password that you have set up in your mySQL config.

What I like to do for mySQL management is use a web-based app called [phpmyadmin]("http://www.phpmyadmin.net/home_page/downloads.php")

you can install it with
```
sudo apt-get install phpmyadmin
```
and i promise it works right after installation. fire-and-forget

---

### Post by Bibiwinter on 2010-04-01
Yep.  Installed without problems and simple to use.  Thanks for that!

I verified the account information and all seems to be ok. I gave the user ipplan with password ipplan all privileges and grant to the ipplan database.  Still refuses to login.

Also verified the ipplan database itself.  The ipplan user is in there with the right privileges in the "privileges" section.  

However, something is still preventing me to login to it through the Web page.  But I tested and I can login to the database with the ipplan user account through the console:

----
root@Ubuntu:~# mysql -u ipplan -p ipplan
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 263
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
---

This looks to me like it's the link between apache/php and mysql that has something wrong and prevents authentication from working.  Missing, wrong or misconfigured package?   Will look into that.

---

### Post by M!K3_$ on 2010-04-01
To be honest, I'm out of ideas. Is it possible to re-do the entire system? I know that's a very "windows" solution, I'm sorry.

Maybe a mySQL expert could get in here and help us out....

---

### Post by BigDXLT on 2010-10-29
Bump for other people having issues installing Ipplan.

I'm on a fresh install of Maverick.  Installed ipplan via the repo's.  I've copied /usr/share/ipplan over to /var/www/ and now get 

[QUOTE="localhost/ipplan"]Problem with database permission or database tables - have installation instructions been followed?

Could not connect to database[/QUOTE]

and

[QUOTE=http://localhost/ipplan/admin/install.php]If you see this message, submit a detailed bug report on Sourceforge including the message below, the database platform used and the steps to perform to recreate the problem.

PHP 5.3.3-1ubuntu9.1 (Linux)
Unknown error type: [2] require_once(/var/www/ipplan/menus/lib/PHPLIB.php): failed to open stream: No such file or directory Line: 554 File: /var/www/ipplan/ipplanlib.php[/QUOTE]

Mysql is up and running, username ipplan works with its password just fine for mysql on its own.

Pretty much looks like the same problem.

---

### Post by BigDXLT on 2010-11-01
For people stumbling around wishing they could just install things and have them Just Work:

Re-reading this helped me:
[https://bugs.launchpad.net/ubuntu/+source/ipplan/+bug/267347](https://bugs.launchpad.net/ubuntu/+source/ipplan/+bug/267347)

Last friday was a long day...  #-o

I uncommented both aliases at the top of "/etc/ipplan/apache.conf", restarted apache and away I went.

A couple other things I stumbled on from there, (log in with the default username password or change it in config.php (can't change it in the program) for the master admin account, add a user, add a group and add the user to that group, then remember "customers" and infrastructure are one in the same) but the documentation cleared all that up for me.  

But anyway, there we go.

---

