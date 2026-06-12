---
title: "Problem with apache2"
date: 2016-02-06
forum: Networking &amp; Wireless
---

### Post by george138 on 2016-02-06
Hello again 

Im trying to change directories in apache2 
I go to cd /etc/apache2/sites-available
Then vim 000-defult.conf
insert
at document Root I changed it to the directory I wanted it to goto which was /home/george/www
esc :x
service apache2 restart
at this I get this error

* Restarting web server apache2                                                   [fail]
 * The apache2 configtest failed.
Output of config test was:
apache2: Syntax error on line 225 of /etc/apache2/apache2.conf: Syntax error on line 29 of /etc/apache2/sites-enabled/000-default.conf: </VirtualHost> without matching <VirtualHost> section
Action 'configtest' failed.
The Apache error log may have more information.

Any Ideas

Thanks

---

### Post by Lordgod on 2016-02-06
Please show us the contents of 000-defult.conf, the configuration may be incorrect.

---

### Post by george138 on 2016-02-06
ome/<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com](www.example.com)


        ServerAdmin webmaster@localhost
        DocumentRoot /home/george/www                                                                                          <<<<< I changed this


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
~
~
~
"000-default.conf" 31L, 1340C

---

### Post by Lordgod on 2016-02-06
What's "ome" at the beginning? written by mistake?
I don't think that's the problem but what are the permissions of this folder /home/george/www ?

---

### Post by george138 on 2016-02-06
oops it is home just didnt copy right

what you mean by permissions
Prior to changing I could see the Its Right or Ok page that apache lets you see when you log in in http now I get [h=1]This webpage is not available[/h]

---

### Post by Lordgod on 2016-02-06
> **george138 said:**
> oops it is home just didnt copy right

what you mean by permissions
Prior to changing I could see the Its Right or Ok page that apache lets you see when you log in in http now I get [h=1]This webpage is not available[/h]

You don't need "home" at the beginning, only <VirtualHost *:80>

run this command to see the permission of the folder:
```
ls -ld /home/george/www
```

---

### Post by george138 on 2016-02-06
root@ubuntuserver:/home/george# ls -ld /home/george/www
drwx------ 3 george george 4096 Feb  5 21:44 /home/george/www
root@ubuntuserver:/home/george#

---

