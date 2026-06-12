---
title: "Localhost Server"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Master_Odin on 2009-07-21
Is there anyway to set-up my computer (so that it uses cPanel, whm, etc.) on a localhost? Would using Ubuntu Server Edition essentially be the best way to go? (and if I do go that route, can I still install/use programs such as Eclipse, OpenOffice.org, etc.?)

I'm essentially installing this on an old laptop so that I can deal with web development in the most accurate workplace situation I can (as lampp just doesn't cut it really when trying to write code that requires something to be set-up). I'll also be using this laptop for my Computer Science classes (and any minor tasks such as word processing) in college if I can.

---

### Post by saj0577 on 2009-07-21
Yeha ubuntu-server is the best and you can install all the same programs but obviously you would need a x server installed on the server to use programs like openoffice,(having a x server on a webserver is not recommended,if installed it should be disabled when not in use.)


YEah if you have a cpanel\whm license you can install it.

I can help with the installation of it all apart from cpanel & whm if thats the route you wish to take.


Saj



AFTER THOUGHT: If the webserver is just for development and not to actually host websites to the public running a x is not a security threat. USing 2 seperate machines for openoffice and the webserver is recommended if possible,understand not always possible.

---

### Post by Master_Odin on 2009-07-21
> **saj0577 said:**
> Yeha ubuntu-server is the best and you can install all the same programs but obviously you would need a x server installed on the server to use programs like openoffice,(having a x server on a webserver is not recommended,if installed it should be disabled when not in use.)


YEah if you have a cpanel\whm license you can install it.

I can help with the installation of it all apart from cpanel & whm if thats the route you wish to take.


Saj



AFTER THOUGHT: If the webserver is just for development and not to actually host websites to the public running a x is not a security threat. USing 2 seperate machines for openoffice and the webserver is recommended if possible,understand not always possible.
Is it a serious issue? Because while I can separate the two onto separate computers, I'd like to keep it all on one laptop if I can as that's one of the reasons I got this particular laptop from a friend.

Also, what would you recommend I do for installing the server?

---

### Post by saj0577 on 2009-07-21
You could run it on the same laptop. If its just a personal website should be fine as you should not be a main target.

So what program you looking to have on the final product and I will write a mini-guide for you.

Saj

---

### Post by Master_Odin on 2009-07-21
> **saj0577 said:**
> You could run it on the same laptop. If its just a personal website should be fine as you should not be a main target.

So what program you looking to have on the final product and I will write a mini-guide for you.

Saj
Nothing on the server will be accessible from the outside. I just want a "realistic" working environment for when I have to try and do something on a clients computer and need to take time to try it out on their server. Would expediate the whole process (as well as give me greater control over various packages available to me within various languages like PHP).

In any case, what do you mean "program you looking to have on the final product"?

---

### Post by saj0577 on 2009-07-21
I.e. when the computer is setup your hoping to have which programs i.e

a webhost
openoffice
cpanel


Saj

---

### Post by Master_Odin on 2009-07-21
> **saj0577 said:**
> I.e. when the computer is setup your hoping to have which programs i.e

a webhost
openoffice
cpanel


Saj
webhost, openoffice, komodo IDE, eclipse (this should be it). I was mentioning cPanel to make a point, but seeing how basically anything that cPanel can do, can be done through terminal, I'll settle for Terminal and get a real feel for what is going on.

---

### Post by saj0577 on 2009-07-21
Webserver Guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


My personal opinion would be to install the ubuntu-desktop edition and uninstall the stuff you dont want as you will also be using it for college work, this will be a much simpler route for you then manuaglly installing an x and then setting up the other programs.


Saj

---

### Post by Master_Odin on 2009-07-21
> **saj0577 said:**
> Webserver Guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


My personal opinion would be to install the ubuntu-desktop edition and uninstall the stuff you dont want as you will also be using it for college work, this will be a much simpler route for you then manuaglly installing an x and then setting up the other programs.


Saj
That was actually exactly what I was looking for! Thanks for the help! :D

---

### Post by Master_Odin on 2009-07-21
> **Master_Odin said:**
> That was actually exactly what I was looking for! Thanks for the help! :D

I'm stuck. I tried going like this:
1) Install apache2
2) Goto [http://localhost](http://localhost) (and I should see a screen that says "It works!" I think...)
3) Install php5 and libapache2-mod-php5
4) Put a file into /var/www to see if it works.

After doing the four steps, I noticed that:
step 2 didn't give me the expected result
step 4 resulted it in giving me an immediate download of the file instead of showing it

Essentially, any file I add to my little "localhost server" can only be downloaded, not actually accessed. The same thing was happening with phpmyadmin after installing it. Help?

---

### Post by Master_Odin on 2009-07-22
Bump?

---

### Post by Master_Odin on 2009-07-23
This is really starting to bug me. I've completely purged apache2 from my computer, then re-installed it and now when I access [http://127.0.0.1](http://127.0.0.1), it opens a dialog to download a file called "default" (which is available in "/etc/apache2/sites-available" It's starting to annoy me that I can't do it.

---

### Post by nimbostratus on 2009-07-23
I remember having this same problem a long time ago but I can't remember how I fixed it.

What did happen after step 2 in your post above?

Can you post your /etc/apache2/httpd.conf file here? That should help. I take it you haven't changed any of the configuration files since installing the apache2 package?

Aaron

---

### Post by Master_Odin on 2009-07-23
> **nimbostratus said:**
> I remember having this same problem a long time ago but I can't remember how I fixed it.

What did happen after step 2 in your post above?

Can you post your /etc/apache2/httpd.conf file here? That should help. I take it you haven't changed any of the configuration files since installing the apache2 package?

Aaron
It appears to be blank O.o

---

### Post by nimbostratus on 2009-07-23
Looking at what libapache2-mod-php5 installs, I think you have it installed but not enabled.

Look in /etc/apache2/mods-available
These two files should be there: php5.conf and php5.load
They are what the package installs.

Look in /etc/apache2/mods-enabled
There should be two softlinks there, with the same names as the above two files and linking to them. When apache starts, it loads everything in this directory, not everything in the mods-available directory.

If those two links aren't there, you can fix your problem by:

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/php5.conf
sudo ln -s ../mods-available/php5.load

EDIT: You'll need to restart apache as well: sudo /etc/init.d/apache2 restart

Hope that helps.
Aaron

---

### Post by Master_Odin on 2009-07-23
Alright, after purging everything from my system, it appears that I finally got it to work. Not sure why it wasn't working, but now it actually goes to the page, and not just shows a download dialog! I guess some remenant was hanging around that was causing it to be fowled up from the first time I tried doing this.

---

