---
title: "folder not showing in localhost"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by kapi on 2010-11-30
hi I've designed a website at work and brought it home via datastick, but after transfering it to the www folder it does not appear in the local host via the browser

help

---

### Post by Wobblybob on 2010-11-30
Have you got an apache server running on the PC in question as the default folder is normally  /var/www/localhost/htdocs

if not, a quick start would be 
 
install apache;

$ sudo apt-get install apache2

Now stop the service with;

$ sudo /etc/init.d/apache2 stop

edit to config file with;

$ sudo gedit /etc/apache2/sites-available/default

and amend the directory path to your site from /var/www/localhost/htdocs to something like  /home/bob/www/localhost/htdocs so that you can find and add docs without being root etc.

And now restart the service with;
$ sudo /etc/init.d/apache2 start

---

### Post by kapi on 2010-11-30
Yeah thanks I'm running LAMP, its really weird its only this one folder that I got from work on a MS pc, I copied it to a datastick and then loaded the new copy on to ubuntu 10.10 in the var/www folder. There is no htdocs and I've been using LAMP for two years now and have only ever seen it when you use xamp.

Maybe its a corrupted file or something, 

thanks again for your comments though.

Right, a quick amendment - it turns out that it was file permissions, so i set them to 777 and now it shows. next problem is my php is being ignored. if it's not one thing its another ;-)

---

