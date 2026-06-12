---
title: "LAMP - Where to start?"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by adamjkok on 2010-07-21
I need to run the Clipperz Community Edition ([clipperz.com]("http://clipperz.com")). It requires (I think) PHP and MySQL. I've heard of LAMP, but I don't know where to start. Here are some of my questions about this:

[LIST]
[*]How do I install LAMP?
[*]How do I use MySQL?
[*]How do I integrate PHP?
[*]How do I change the port (my ISP blocks running servers on port 80, I want either 8080 or something more obscure so that they don't figure it out, suggestions are welcome)?
[*]How do I control the server?
[/LIST]
Note: I'm running the DESKTOP EDITION, I use this computer as more than just a server.

---

### Post by bodhi.zazen on 2010-07-21
IMO this is a good place to start

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Once you have gotten a start come on back with more specific questions.

---

### Post by sandyd on 2010-07-22
to install LAMP, run ```
tasksel
``` in a terminal. use the arrow keys to select "lamp server". Press the spacebar, then use the tab key to navigate over to the "ok" button. Press enter. When youre done that step post back. ps, dont forget your mysql root password that it will ask you to set.

---

### Post by EmmyS on 2010-07-22
I'm not the original poster, but I also have a question about this. I've read the link you posted, and it mentions installing from the Ubuntu server edition CD. Do you have to be running the server edition to install LAMP? I'm looking to set up a development environment, strictly localhost, and would like to be able to run one of the desktop or netbook editions of Ubuntu.

---

### Post by ridgeland on 2010-07-22
I'm stuck too. Ubuntu 10.04 - 64 bit
I used:
$ sudo apt-get install lamp-server^
(Don't know what the ^ means)
When I point Firefox to localhost
I get the It Works! page (simple html, but apache works)
When I try a page with php - nothing.
When I view page source I see the <?php ..... ?> nothing was translated it's still raw in the page source.
From bodhi.zazen's link trouble shooting php5
Verified with synaptics that libapache2-mod-php5 is installed.
$ sudo a2enmod php5
Module php5 already enabled
$ sudo /etc/init.d/apache2 restart
Still raw <?php... doesn't run.
I can go to my home page which uses php and the script runs fine on that host so I don't think it's a Firefox setting.
What am I missing?
(MySQL works great from the terminal, gotta get php working next)

---

### Post by bodhi.zazen on 2010-07-22
> **EmmyS said:**
> I'm not the original poster, but I also have a question about this. I've read the link you posted, and it mentions installing from the Ubuntu server edition CD. Do you have to be running the server edition to install LAMP? I'm looking to set up a development environment, strictly localhost, and would like to be able to run one of the desktop or netbook editions of Ubuntu.

You can run apache or other "server software" on a desktop if you wish.

Some people use xammp

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by bodhi.zazen on 2010-07-22
> **ridgeland said:**
> I'm stuck too. Ubuntu 10.04 - 64 bit
I used:
$ sudo apt-get install lamp-server^
(Don't know what the ^ means)
When I point Firefox to localhost
I get the It Works! page (simple html, but apache works)
When I try a page with php - nothing.
When I view page source I see the <?php ..... ?> nothing was translated it's still raw in the page source.
From bodhi.zazen's link trouble shooting php5
Verified with synaptics that libapache2-mod-php5 is installed.
$ sudo a2enmod php5
Module php5 already enabled
$ sudo /etc/init.d/apache2 restart
Still raw <?php... doesn't run.
I can go to my home page which uses php and the script runs fine on that host so I don't think it's a Firefox setting.
What am I missing?
(MySQL works great from the terminal, gotta get php working next)

In firefox, clear you cache

---

### Post by EmmyS on 2010-07-22
> **bodhi.zazen said:**
> You can run apache or other "server software" on a desktop if you wish.

Some people use xammp

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Thank you! I'm new to Linux, and I have an EasyPHP install on my WinXP machine, so  xammp is exactly the kind of thing I was looking for - an all-in-one solution.

---

### Post by mcduck on 2010-07-22
> **ridgeland said:**
> I'm stuck too. Ubuntu 10.04 - 64 bit
I used:
$ sudo apt-get install lamp-server^
(Don't know what the ^ means)
When I point Firefox to localhost
I get the It Works! page (simple html, but apache works)
When I try a page with php - nothing.
When I view page source I see the <?php ..... ?> nothing was translated it's still raw in the page source.
From bodhi.zazen's link trouble shooting php5
Verified with synaptics that libapache2-mod-php5 is installed.
$ sudo a2enmod php5
Module php5 already enabled
$ sudo /etc/init.d/apache2 restart
Still raw <?php... doesn't run.
I can go to my home page which uses php and the script runs fine on that host so I don't think it's a Firefox setting.
What am I missing?
(MySQL works great from the terminal, gotta get php working next)

Did you actually move the .php file to the web root directory? (/var/www/ by default).

Having PHP installed doesn't allow you to open PHP files directly, they still have to be processed by the web server, as PHP is a server-side scripting language. Just move your .php file into /var/www and point your browser to [http://localhost](http://localhost) and you should see the results. :)

---

### Post by ridgeland on 2010-07-22
I'm still fishing for a solution.
My simple little test html is:
```
<html><head><title>My First PHP Page</title></head><body>
PHP start<br>
<?php
phpinfo();
?>
PHP end
</body></html>
```
My output is only:
PHP start
PHP end
I've cleared cache and used new htmls that could not be in cache.  I've changed permissions to 777, even run Firefox as root.
I've tried on Ubuntu 10.04 (couple of installs), Ubuntu 10.04 server (with ubuntu.desktop installed), Ubuntu 9.04 and Mandriva 2010.1 (Spring).  SuSE 11.3 and I didn't get far.
Mandriva/Firefox will load myphpadmin.php without complaining. But still the php scripts are not running.  All the Ubuntus balk at *.php and ask what to use to load it.
I uploaded the script to my web hosting site and it runs fine.  Between PHP start and PHP end I get screens and screens of tables like I expect.
php5-cli works. I can run a "Hello, World!" script, even phpinfo() spills screens of text.
Next tests will be trying a different PC.  I remember doing this a couple of years back and phpinfo() worked on localhost for me.  I keep thinking it must be as simple as missing a ";".
I did move the file to /var/www/ (Mandriva uses /var/www/html/)

---

### Post by phillw on 2010-07-22
Hi,

there is going to be a session on adding LAMP over on the #ubuntu-classroom 

[http://people.ubuntu.com/~nhandler/classroom.html](http://people.ubuntu.com/~nhandler/classroom.html)

on [http://timeanddate.com/worldclock/fixedtime.html?month=7&day=28&year=2010&hour=18&min=0&sec=0&p1=0](http://timeanddate.com/worldclock/fixedtime.html?month=7&day=28&year=2010&hour=18&min=0&sec=0&p1=0)

I am also going to tidy up [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to split it from people who want to add LAMP to their desktop system as opposed to those who want a pure server system.

So, please be patient; it is going to happen. In the meantime, if there is anything that cannot wait, you can grab a hold of me via my profile [https://wiki.ubuntu.com/phillw](https://wiki.ubuntu.com/phillw)

:popcorn:

Regards,

Phill.

---

### Post by ridgeland on 2010-07-23
Finally cracked my problem with no php in html.
It's that way by default!  My patch is here:
[PHP not working in *.html in LAMP]("http://ubuntuforums.org/showthread.php?t=1537679")

Thanks adamjkok for this Thread.  How are you progressing?  My next steps will be trying to get the M in LAMP to work with the A and P.

---

