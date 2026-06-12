---
title: "Apache2 and default DocumentRoot Help Please"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by drhiii on 2007-06-09
I've searched the forums and haven't found the answer... so hopefully someone can help.

How do I change the default DocumentRoot location in Apache2.  It defaults of course to /

home/*/public_html

And I would like to change this to something like    /home/*/public_html/cms   or some similar change.

I have changed over to Ubuntu which is a Debian foundation, and it is somewhat different that the RedHat/Apache structure I am more familiar with...  

Help anyone?

drhiii

---

### Post by dfreer on 2007-06-09
Actually, the default document root (e.g. [http://localhost/](http://localhost/) ) would be /var/www/
The document root for individual users is /home/$USER/public_html, (e.g. http://localhost/~$USER/ )
(where $USER is the name of the your user)

You can change the actual document root by editiing this file:
/etc/apache2/sites-enabled/000-default/

Find this section (might be slightly different from mine):
```
<VirtualHost *>
        ......
        DocumentRoot **/var/www**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory **/var/www/**>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        .......
</VirtualHost>

```

Change the directories highlighted in **bold** if you want to change the DocumentRoot for the main server.



To change the individual user's document roots, edit this file:
/etc/apache2/mods-available/userdir.conf

```

<IfModule mod_userdir.c>
        UserDir **public_html**
        UserDir disabled root

        <Directory **/home/*/public_html**>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>
</IfModule>

```

I believe you change the two files highlighted in **bold**, BUT I'm not quite sure (makes sense though). After editing either file you will most likely need to restart the serrver so it can recognize the changes with this command:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by drhiii on 2007-07-02
Thank you for this response.  Just received (never got a notification).... this is very helpful.

drhiii

> **dfreer said:**
> Actually, the default document root (e.g. [http://localhost/](http://localhost/) ) would be /var/www/
The document root for individual users is /home/$USER/public_html, (e.g. http://localhost/~$USER/ )
(where $USER is the name of the your user)

You can change the actual document root by editiing this file:
/etc/apache2/sites-enabled/000-default/

Find this section (might be slightly different from mine):
```
<VirtualHost *>
        ......
        DocumentRoot **/var/www**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory **/var/www/**>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        .......
</VirtualHost>

```

Change the directories highlighted in **bold** if you want to change the DocumentRoot for the main server.



To change the individual user's document roots, edit this file:
/etc/apache2/mods-available/userdir.conf

```

<IfModule mod_userdir.c>
        UserDir **public_html**
        UserDir disabled root

        <Directory **/home/*/public_html**>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>
</IfModule>

```

I believe you change the two files highlighted in **bold**, BUT I'm not quite sure (makes sense though). After editing either file you will most likely need to restart the serrver so it can recognize the changes with this command:
```
sudo /etc/init.d/apache2 restart
```

---

