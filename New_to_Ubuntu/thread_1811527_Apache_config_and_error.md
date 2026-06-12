---
title: "Apache config and error"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by zanzibarwinds on 2011-07-25
Hi

I set up a LAMP install on Ubuntu 11.04 which is running on my PC within Virtual Box but have a few niggiling issues with the way its set up.

The dev environment is such that I run VBox but do my development on Windows via Zend Studio.

The website I work on at the time have its public_html folder shared from Samba so I can access the files fine.

My issues are as follows:

1.    When browsing to the development site from Windows I have to use the URL [http://john-virtualbox/supply/public_html/](http://john-virtualbox/supply/public_html/)

The location of the files on the VBox machine is /var/www/supply/public_html/

I’d like this to rather be closer to a live environment so that the URL is [http://john-virtualbox/supply/](http://john-virtualbox/supply/)

No amount of fiddling with the file for this site seems to get me to do this. The files within /etc/apache2/sites-available/ are as follows:

Notes: /etc/apache2/sites-anabled/ folder is empty apart from a file named 000-default

default

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www
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

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Supply

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/supply/public_html
    ServerName supply
    <Directory />         
        Options FollowSymLinks         
        AllowOverride None         
        IndexIgnore */*     
    </Directory>     
    
    <Directory /var/www/supply/public_html>         
        Options Indexes FollowSymLinks MultiViews         
        AllowOverride None         
        Order allow,deny         
        allow from all     
    </Directory>  
</VirtualHost>


2. I wasnt getting php errors showing so mader the php.ini change for this and restarted apache2 as follows and got an error which might be the cause of some issue realted to point 1.

john@john-VirtualBox:~$ sudo  /etc/init.d/apache2 reload
[sudo] password for john: xxxxxxxxxx
 * Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

3. Lastly, related to permissions. The dev site has a browser upload for images. Whenever I use the upload it didnt upload files until I used Samba and simply shared the /images/ folder with Read/Write permissions for everyone. Prior to this I used to open nautilus and simply right click on the folder and give R/W access to everyone as eoot.

Not ideal, is there any literature on how to correcdtly set up permissions for a directory that needs to allow uploads for the "www_data" user which I think is the user for web users.

Thanks for any help with these.
John

---

### Post by zanzibarwinds on 2011-07-29
Hi

Dont suppose anyone can help me on this or point me in the direction of some decent literature.

Ta
John

---

### Post by sadaruwan12 on 2011-07-29
First of how did you install your LAMP server did you do it manually or used the tasksel commend please let us know.

And here is what I used to get help and now my LAMP is running with out any issue.

Also I think it's better if you move your default public_html to a personal path the help page have a segment how to do that I did it and works like a charm.

[Click]("https://help.ubuntu.com/community/ApacheMySQLPHP") here to go there

---

