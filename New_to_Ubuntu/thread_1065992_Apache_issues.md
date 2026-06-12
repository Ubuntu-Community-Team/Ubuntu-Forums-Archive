---
title: "Apache issues"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Cyked on 2009-02-10
Not sure if the is the right place....


I installed apache on my ubuntu system, and it seemed to be working fine.  I could get to the site externally (I'm using dyn dns for my IP) with no issues.  Beyond just the web page I have several directories (images and such).  I have a directory of /pics, which is fine, and a directory /gifs which does not function correctly.  When going to that dir in IE/FF it displays one of the animated gifs in the directory instead of showing the contents of the directory like the /pics dir does.

What gives?

---

### Post by minsf on 2009-02-10
please post here the content of the file /etc/apache2/sites-available/default and also the contents of the directory /gifs. what is the name of the file it plays when you go to /gifs?

---

### Post by minsf on 2009-02-10
also, how did you install apache? did you install it via the lamp-server metapackage?

---

### Post by Cyked on 2009-02-10
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>








Here is what I see in the directory.  The gif file that is the issue _was _named index.php.gif.  I renamed it to animation.gif and I still have the issue.  The image in question shows as path [http://servname.homeip.net/files/gifs/](http://servname.homeip.net/files/gifs/) where normally it would show as [http://servname.homeip.net/files/gifs/animation.gif](http://servname.homeip.net/files/gifs/animation.gif).

If I put in the address bar 
[http://servname.homeip.net/files/gifs/image1.gif](http://servname.homeip.net/files/gifs/image1.gif) it will show the gif.  I just can't see the gifs directory like I can on the other directories residing on the server.


On the install I just did a apt-get install apache

---

### Post by minsf on 2009-02-10
> **Cyked said:**
> 
Here is what I see in the directory.  The gif file that is the issue _was _named index.php.gif.  I renamed it to animation.gif and I still have the issue.

did you try refreshing the browser's cache after you renamed the index gif file?
what files do you see in the directory /etc/apache2/sites-enabled/ ? do you have a configuration file named "servname" there? if you do, please post it's content (notice that it is just a symbolic link, and the "real" file is located in /etc/apache2/sites-available/ with the same name. the symlink just enables that particular configuration)

---

### Post by Cyked on 2009-02-10
File: 000-default in the sites-enabled

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch


I don't see a servname file under sites-enabled.

---

### Post by minsf on 2009-02-10
weird... this looks fine. you have "Options Indexes" in the configuration of /var/www/ so this means you should have indexing for this directory and all its subdirectories. 
/gifs is a subdirectory of /var/www on your system, right?

have you tried refreshing the browser cache (ctrl+r)?
have you tried restarting apache? in the command line enter ```
sudo /etc/init.d/apache2 restart
```
and let us know if you get any error as an output of this.

would you be able to post here the configuration of your server (the file /etc/apache2/apache2.conf ?

---

### Post by Cyked on 2009-02-11
Last night when I got home I moved the file out of the directory and it worked fine on my iphone.  I checked in the office this morning, and it's working fine on my work machine.  *shrug*

---

### Post by minsf on 2009-02-12
> **Cyked said:**
> Last night when I got home I moved the file out of the directory and it worked fine on my iphone.  I checked in the office this morning, and it's working fine on my work machine.  *shrug*
glad to hear things are working for you now. let us know if you still have problems to make it work on your home box
cheers :)

---

