---
title: "will not read php5 extension in apache2"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by Tom of Helatrobus on 2010-09-19
Just did a reinstall of ubuntu on the laptop. Had to make a dual top with Windows (gag - I had some stuff that just wouldn´t run on vine). Reinstalled apache, mysql, php5, etc. However, my php5 files will not work with localhost, although the php files do. I can´t just change the files to php, because the server of the site I do volunteer webmastering on will only read php5 files. 

I know there is a solution for this using addhandler or addtype in a configuration file (because I did it before and had it working before the reinstall) I just can´t remember how I did it - maybe the httpd.conf or phpmyadmin.conf?. Also I´m sure a .htaccess file might fix it, but my attempts so far haven´t worked. I know this is just a simple matter of using sudo nano in a terminal to change a few lines of code - PLEASE point the way.

---

### Post by sandyd on 2010-09-19
> **Tom of Helatrobus said:**
> Just did a reinstall of ubuntu on the laptop. Had to make a dual top with Windows (gag - I had some stuff that just wouldn´t run on vine). Reinstalled apache, mysql, php5, etc. However, my php5 files will not work with localhost, although the php files do. I can´t just change the files to php, because the server of the site I do volunteer webmastering on will only read php5 files. 

I know there is a solution for this using addhandler or addtype in a configuration file (because I did it before and had it working before the reinstall) I just can´t remember how I did it - maybe the httpd.conf or phpmyadmin.conf?. Also I´m sure a .htaccess file might fix it, but my attempts so far haven´t worked. I know this is just a simple matter of using sudo nano in a terminal to change a few lines of code - PLEASE point the way.
its in httpd.conf

the line will have the words
AddHandler php ****
so just press control + W and search for it from there.

Since I haven't used ubuntu for some time now, it could also be in the php config file, which is in the enabled extensions folder (also in /etc/apache2)

---

### Post by Tom of Helatrobus on 2010-09-20
> **sandyd said:**
> its in httpd.conf

the line will have the words
AddHandler php ****
so just press control + W and search for it from there.

Since I haven't used ubuntu for some time now, it could also be in the php config file, which is in the enabled extensions folder (also in /etc/apache2)

Strangest thing. I looked at my httpd.conf file and it was completely empy - There was nothing in it at all!!! I guess I´ll look for a new one.

---

### Post by Tea-Man on 2010-09-20
> **Tom of Helatrobus said:**
> Strangest thing. I looked at my httpd.conf file and it was completely empy - There was nothing in it at all!!! I guess I´ll look for a new one.

Yeah, that's right (was suprised by that as well :p). I believe since some versions ago, it doesn't work with the httpd.conf file anymore, but with the apache2.conf (had some problems with apache2 as well, fixed it by editing that file). So it might just be in there.

Other things you might look at:
- there is a php5.conf file in  /etc/apache2/mods-enabled that seems to do something with the file-extension.
- I guess adding/editing the .htaccess file to the webhosting (if you have access to it...) telling server to handle .php files as well.

Well, good luck with all that!


BTW: you could write a small program in php as well to rename all the files to .php5 and back to .php :P

---

### Post by SeijiSensei on 2010-09-20
You can place the AddHandler directive in a .htaccess file in the root directory of the website.  

AddHandler php5-script .php5

More details here:
[http://httpd.apache.org/docs/1.3/mod/mod_mime.html#addhandler](http://httpd.apache.org/docs/1.3/mod/mod_mime.html#addhandler)

---

### Post by Tom of Helatrobus on 2010-09-20
> **SeijiSensei said:**
> You can place the AddHandler directive in a .htaccess file in the root directory of the website.  

AddHandler php5-script .php5

More details here:
[http://httpd.apache.org/docs/1.3/mod/mod_mime.html#addhandler](http://httpd.apache.org/docs/1.3/mod/mod_mime.html#addhandler)

When with the above solution: 

1. open terminal
2. (navigated to directory) cd /var/www
3. sudo nano, then a password (to open new document in terminal)
4. wrote in the following text: 

#----------  read the php5 extension ---------
AddHandler php5-script .php5

5. saved by pressing control x, then y to confirm. Then saved as ¨.htaccess¨
6. in terminal: sudo /etc/init.d/apache2 stop (to stop apache)
7.sudo /etc/init.d/apache2 start (to start apache)

This seems like the simplest way. Thanks for all the suggestions and help.

---

### Post by Tom of Helatrobus on 2010-09-27
An after thought here. I was reinstalling apache2 in ubuntu 10.4 and apache2 was NOT reading the .htaccess file. See this link for more information: [http://ubuntuforums.org/showthread.php?t=47669](http://ubuntuforums.org/showthread.php?t=47669)

 For some reason apache2 does not allow .htaccess files as a default setting. you must access /etc/apache2/sites-available/default 

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        **AllowOverride All**
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

```change the ¨AllowOverride None¨ to ¨AllowOverride All¨ - case sensative btw. I used terminal and gedit to get there and make the changes:

```

thomas@thomas-laptop:~$ cd /etc/apache2/sites-available
thomas@thomas-laptop:/etc/apache2/sites-available$ sudo gedit default

```

---

