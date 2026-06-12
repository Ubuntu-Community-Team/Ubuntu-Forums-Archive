---
title: "Help!  No Apache2 after new kernel dowload!"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Kellemora on 2010-04-29
Hi Gang

Host unreachable:
IP is CORRECT:

Worked fine until the kernel upgrade this morning!
Been trying to get it working ever since!

Getting the following error message in Terminal.
"apache2: Syntax error on line 301 of /etc/apache2/apache2.conf:  Could not open configuration file /etc/phypmyadmin/apache.conf:  No such file or directory [fail]"

I have NEVER touched ANY configuration files!!!!!
Just installed the stuff for LAMP to do my php lessons and it worked out of the box!  Has worked perfectly for my needs until the automatic update of the kernel this morning.  Now it's BROKE!

And that is the extent of my knowledge about servers too!
Tried sudo /etc/init.d/apache2 restart (also start).

HELP!

TTUL
Gary

---

### Post by bodhi.zazen on 2010-04-29
Are you using phpmyadmin ?

Was it removed ?

I would not assume this is a kernel upgrade problem, it appears to be an apache configuration problem.

---

### Post by Kellemora on 2010-04-29
Hi Bod

As you know from my other posts, I'm more like Schultz "I KNOW NOTHING!"

I merely installed Apache, MySQL and PHP, it worked out of the box!
Have had no problems connecting to my testing web pages I'm working on.
UNTIL, I got the automatic update this morning.  Rebooted after that of course, and now it's BROKE........

I may or may not have loaded phpmyadmin when I loaded the server, but if I did, I've never used it yet, don't know how!

I'm a totally lost NOOB here, when it comes to this new server I installed to do my lessons on.

TTUL
Gary

Edited to add:  I could go into synaptic I guess and uninstall everything and reinstall it all again?????  Since it worked out of the box once, it may work out of the box again?

Just checked synaptic, phpmyadmin was NOT installed.  So I checked it, now I have a box on the screen that says, Configuring phpmyadmin with 5 checkboxes on it.  Do I check All of them, none of them, or only apache2?

---

### Post by bodhi.zazen on 2010-04-29
Probably the easiest thing to do would be to simply (re)install phpmyadmin. I assume you have installed and removed it (just a guess).

```
sudo apt-get isntall phpmyadmin
```

Then try to start apache again

```
sudo service apache2 restart
```

The longer answer would involve manually editing apache config files, which is not too difficulet, but most people prefer a wirking server first, play with broken config files second.

Your other option would be to simply purge and re-install apache

```
sudo apt-get purge apache2
sudo apt-get install apache2
```

But , if you do that, back up /var/www (and any other config files you want to keep) first.

---

### Post by Kellemora on 2010-04-29
Hi Bod

phpmyadmin was NOT installed, so I installed it.
After doing so, a RESTART of Apache2 seemed to work.
I can now access my lessons files from any computer.

However, trying to bring up phpmyadmin using /localhost/www/phpmyadmin said page not found.

In any case, the server is now running so I can get to my lessons.

Thanks for your help!

TTUL
Gary

---

### Post by bodhi.zazen on 2010-04-29
try 

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by Kellemora on 2010-04-29
Hi Bod

That did the trick, thank you!

Wouldn't take my password, but I got in leaving that line blank.

Could not find any way to set a password, so will have to study that too!

Find out what phpmyadmin is for too, as far as that goes.

As I said, I'm in WAY over my head!
But figure I will eventually learn like everyone else!
Perhaps a little slower though, hi hi......

Again, thanks for all your help!

TTUL
Gary

---

### Post by Geoff918 on 2010-04-29
This is right on point:

[http://www.cyberciti.biz/faq/mysql-change-root-password/](http://www.cyberciti.biz/faq/mysql-change-root-password/)

Don't bother with the "root" thing, though. Logging in as yourself (own user) should be good enough--as long as you have superuser privilege.

---

### Post by Kellemora on 2010-05-04
Thanks Geoff

I printed that page out and placed it in my paper LAMP folder.
Set the password as suggested also.

TTUL
Gary

---

