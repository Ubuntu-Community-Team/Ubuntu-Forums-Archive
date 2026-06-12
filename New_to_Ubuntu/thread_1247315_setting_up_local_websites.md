---
title: "setting up local websites"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by rmiwiw on 2009-08-22
I am trying to set up a VirtualHost for my local Ubuntu Server (9.04).

Ideally I want to do the following. I want to have different urls for each of the local projects I am working on.

[FONT=Courier New]http://localhost
[http://books](http://books)
[http://calendar](http://calendar)[/FONT]

These are just examples.

******First, I must point out that I have named my server different than localhost or whatever is standard.  When I installed the server I gave it a name, let's say I called it '[FONT=Courier New]SamTheServer[/FONT]'[INDENT] Currently (even before I started making VirtualHosts) I could NOT get the localhost website to come up ([FONT=Courier New]http://localhost[/FONT]).  I could, however, get [FONT=Courier New]http://samtheserver[/FONT] to come up. 
[/INDENT]With that said I have taken the [FONT=Courier New]default [/FONT]file in [FONT=Courier New]sites-available[/FONT] and copied to make a new file '[FONT=Courier New]books[/FONT]'. I have kept everything the same except I have changed the [FONT=Courier New]/var/www/[/FONT] path to be in the home directory of my user account (there are two places to change this and I have done both). Secondly I have added the '[FONT=Courier New]ServerName books[/FONT]' line to the file.

The next step is that I then entered this '[FONT=Courier New]a2ensite books[/FONT]' (to enable the site and send it to the [FONT=Courier New]sites-enabled[/FONT] folder (this makes an [FONT=Courier New]ln -s [/FONT]link back to the [FONT=Courier New]sites-available[/FONT] folder).

After I reloaded and restarted apache I got nothing. It would just connect me to a search online. I pinged my new '[FONT=Courier New]books[/FONT]' site and it looks like packages are being sent and such but no website is viewable.

Below are the contents of my files.

_**/etc/hosts **_
(some places have said to edit this, but I ended up taking everything out that wasn't there originally)

```

127.0.0.1       localhost
127.0.1.1       SamTheServer.domain.actdsltmp      SamTheServer

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```_**/etc/apache2/sites-available/books**_
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName books
        DocumentRoot /home/user/projects/Books
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/tiffy/projects/Books/>
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

        ErrorLog /var/log/apache2/books-error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/books-access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

```

---

