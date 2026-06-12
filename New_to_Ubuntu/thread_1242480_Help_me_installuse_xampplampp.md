---
title: "Help me install/use xampp/lampp"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by Kezz Kezz on 2009-08-17
Hi all,

I've installed ubuntu on my pc as it was running a very old and dodgy windows xp and almost unusable. The install seemed to go ok except I can't get any sound (and have no driver discs for any of my hardware).

What I want to do now is install xampp. I've tried doing it through the terminal but keep hitting dead ends when I get an error message and the tutorial's don't cover it. I finally made some progress by dropping on a tip in another thread here. 

From [http://ubuntuforums.org/showthread.php?t=1196689&page=2](http://ubuntuforums.org/showthread.php?t=1196689&page=2)
> **jimv said:**
> 

Here's what you do...this will install Apache, Mysql, and PHP:

Go to System > Administration > Synaptic Package Manager

Go to Edit > Mark Packages by Task

Put a check on "LAMP Server" and click OK

Click Apply.  

This will install everything you need to develop/use web apps that use PHP/MySQL. It's pretty much the same thing as XAMPP, but without all the hassle, and the applications will also stay up-to-date.

But what do I do next? If I just go into firefox and type localhost I get a screen saying "It works" 

What did I miss? :confused:

---

### Post by mcduck on 2009-08-17
Nothing, you now have a working Apache setup. :)

In case you are wondering, the web root directory (where you put your web files) is /var/www, and all Apache configurations can be found in /etc/apache2.

This guide should be helpful: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Dithers on 2009-08-17
Then... it works
you can go to 

[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

to access phpmyadmin if its installed as well

---

### Post by Kezz Kezz on 2009-08-17
oh right, ok. I've used wamp before and I thought you got a screen up using localhost....

Anyway, localhost/phpmyadmin gives 
> **Not Found**

  The requested URL /phpmyadmin was not found on this server.
   Apache/2.2.11 (Ubuntu) Server at localhost Port 80
[FONT=Arial]
[/FONT]

So I need to install that too I guess.....
[FONT=Arial]
[/FONT]

---

### Post by mcduck on 2009-08-17
> **Kezz Kezz said:**
> oh right, ok. I've used wamp before and I thought you got a screen up using localhost....

Anyway, localhost/phpmyadmin gives 


So I need to install that too I guess.....
[FONT=Arial]
[/FONT]

Only if you want a web-based administration interface for your MySQL databases.

---

### Post by Kezz Kezz on 2009-08-17
I'm trying to get to a stage where I can create a development environment to use joomla to make a website...... I'm struggling to get phpmyadmin now.


ETA: Oo Oo Oo I think I've done it! I'm now getting a php welcome page *dances around room*

---

