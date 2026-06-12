---
title: "How to setup apache"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by lkytmr on 2009-01-07
Sorry for being such an idiot here but the forum title is absolute beginners so I thought I would give it a whirl. Due to layoffs, our resident nerd is now gainfully employed elsewhere and I have become the defacto wiki and website monster-sitter.

I need to add another website to our web server and all the explanations on the web seem very complicated.

1. For starters, there seem to be two identical files for our website, one in sites-enabled and one in sites-available. 

Why two and what is the difference?

2. There is an include directive in my apache2.cnf:

include /etc/apache2/sites-enabled 

Does this automatically include all files in the sites-enabled directory?

3. Can I just copy the config files from the sites-enabled and sites-available directories to a new site-name, and then copy the directory that these refer to to a new directory and then start modifying from there?

Hopefully my questions make at least minimal sense.

Thanks in advance for any help.

:confused:

---

### Post by halitech on 2009-01-07
the sites-available folder is a list of sites that could be served from the server, sites-enabled is the list of actual sites that are being served. basically you take the info in sites-available and create a new site (save the file with a new name ie. site2) and make the changes you need (ie directory where the files will reside)

then as root you enable it
```
sudo a2ensite
```
it will then ask what site to enable and type in the new name of the site
you will need to restart apache in order to see the changes on your server

---

### Post by Iowan on 2009-01-07
I'd have to check my server at work, but on my home LAMP server, the /etc/apache2/sites-enabled directory contains a link to the file in  /etc/apache2/sites-available.

Just to pass on some (hopefully useful) information: [http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/")
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Randy3011 on 2009-01-07
Hi:
Hope the following helps:

[http://www.howtoforge.com/perfect-server-ubuntu-8.10]("http://www.howtoforge.com/perfect-server-ubuntu-8.10")

Good Luck,
Randy3011

---

### Post by lkytmr on 2009-01-08
Three responses in one day!

Thanks people. I will try to digest your information and see what happens.

Thanks for your input and I'll let you know what happens.

Tom

---

### Post by lkytmr on 2009-01-08
I think my problem is even more fundamental than configuring apache.

I have a domain name of epc-inc.com.

We have a working website at [www.epc-inc.com](www.epc-inc.com).

The files for this website are in our var/www/epc directory.

When I browse to [http://www.epc-inc.com/](http://www.epc-inc.com/) I go to the correct website.

Now:

sudo cp -r /var/www/epc /var/www/tmr

Now i edit /var/www/tmr/index.htm and change it.

etc/apache2/epc looks as follows:

<VirtualHost *:80>
        ServerName epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]
        Redirect permanent / [http://www.epc-inc.com/](http://www.epc-inc.com/)
</VirtualHost>

<VirtualHost *:80>
        ServerName [www.epc-inc.com](www.epc-inc.com)
        ServerAdmin [email]admin@epc-inc.com[/email]
        #ErrorDocument 404 /error404.html

        DocumentRoot /var/www/epc
        Options -ALL
        <Directory />
                AllowOverride None
                Order deny,allow
                deny from all
        </Directory>
        <Directory /var/www/epc>
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

My wiki site looks as follows:

#EPC Wiki virtual host
<VirtualHost 192.168.2.10:443>
        ServerName wiki.epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]

        #Enable SSL
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/wiki.crt
        SSLCertificateKeyFile /etc/apache2/ssl/wiki.key

        DocumentRoot /var/www/mediawiki-1.13.2

        <Directory />
                Options -All
                AllowOverride None
                Order Deny,Allow
                Deny from all
        </Directory>
        <Directory /var/www/mediawiki-1.13.2>
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>




Now:

sudo cp /etc/apache2/epc /etc/apache2/tmr

Now modify /etc/apache2/tmr as follows:

<VirtualHost *:80>
        ServerName tmr.epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]
</VirtualHost>

<VirtualHost *:80>
        ServerName tmr.epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]
        #ErrorDocument 404 /error404.html

        DocumentRoot /var/www/tmr
        Options -ALL
        <Directory />
                AllowOverride None
                Order deny,allow
                deny from all
        </Directory>
        <Directory /var/www/tmr>
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

Then enable the site and try browsing to tmr.epc-inc.com with no luck.

I realize that there is something fundamental that I don't understand. 

Thanks
Tom

---

### Post by lkytmr on 2009-01-08
I think my problem is even more fundamental than configuring apache.

I have a domain name of epc-inc.com.

We have a working website at [www.epc-inc.com](www.epc-inc.com).

The files for this website are in our var/www/epc directory.

When I browse to [http://www.epc-inc.com/](http://www.epc-inc.com/) I go to the correct website.

Now:

sudo cp -r /var/www/epc /var/www/tmr

Now i edit /var/www/tmr/index.htm and change it.

etc/apache2/epc looks as follows:

<VirtualHost *:80>
        ServerName epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]
        Redirect permanent / [http://www.epc-inc.com/](http://www.epc-inc.com/)
</VirtualHost>

<VirtualHost *:80>
        ServerName [www.epc-inc.com](www.epc-inc.com)
        ServerAdmin [email]admin@epc-inc.com[/email]
        #ErrorDocument 404 /error404.html

        DocumentRoot /var/www/epc
        Options -ALL
        <Directory />
                AllowOverride None
                Order deny,allow
                deny from all
        </Directory>
        <Directory /var/www/epc>
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

My wiki site looks as follows:

#EPC Wiki virtual host
<VirtualHost 192.168.2.10:443>
        ServerName wiki.epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]

        #Enable SSL
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/wiki.crt
        SSLCertificateKeyFile /etc/apache2/ssl/wiki.key

        DocumentRoot /var/www/mediawiki-1.13.2

        <Directory />
                Options -All
                AllowOverride None
                Order Deny,Allow
                Deny from all
        </Directory>
        <Directory /var/www/mediawiki-1.13.2>
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>




Now:

sudo cp /etc/apache2/epc /etc/apache2/tmr

Now modify /etc/apache2/tmr as follows:

<VirtualHost *:80>
        ServerName tmr.epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]
</VirtualHost>

<VirtualHost *:80>
        ServerName tmr.epc-inc.com
        ServerAdmin [email]admin@epc-inc.com[/email]
        #ErrorDocument 404 /error404.html

        DocumentRoot /var/www/tmr
        Options -ALL
        <Directory />
                AllowOverride None
                Order deny,allow
                deny from all
        </Directory>
        <Directory /var/www/tmr>
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

Then enable the site and try browsing to tmr.epc-inc.com with no luck.

I realize that there is something fundamental that I don't understand. 

Thanks
Tom

---

### Post by halitech on 2009-01-09
Hi Tom

things look fine to me and when I try the tmr site, this is what I get

hello world
My name is Tom and I am 51 years old
olah el mundo
Click aqui

---

