---
title: "Apache &amp; Gnump3d on port 80"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by ScottVickery on 2006-08-28
Hey there, I am configuring my first linux server in a long time.  If this ends up on the wrong list or, I could have found this in a FAQ somewhere, my apologies in advance.

I want to run both Apache and Gnump3d on port 80 because most other ports at my day job are blocked.  Can I configure Gnump3d as a plugin for Apache?  Or, is there perhaps a better solution to allow be streaming mp3's through Apache?

Thanks,
Scott Vickery

---

### Post by moldham on 2008-01-31
You can try the following configuration to see if this helps. 

- First you will need to set gnump3d to run on a port other than port 80 in '/etc/gnump3d/gnump3d.conf'. 
- Next you will need to add a configuration similar to the following to apache:

<VirtualHost *:80>
        ServerAdmin [email]MusicAdmin@domain.com[/email]
        ServerName music.domain.com
        ServerAlias music.domain.com  <server_ip>

        CustomLog /var/log/apache2/music.domain.com-access.log combined
        ErrorLog /var/log/apache2/music.domain.comt-error.log
        SuexecUserGroup apache apache

        DocumentRoot "/default/music/directory"

        <Directory "/default/music/directory">
                Order Deny,Allow
                Deny from all
        </Directory>

        RewriteEngine On

        <Location />
                Order Deny,Allow
                Deny from all
                AuthName "Authenication Required "
                AuthType Basic
                #AuthBasicProvider file
                AuthUserFile /default/music/directory/.htpasswd
                Require valid-user
                Satisfy any
        </Location>

        ProxyPass / [http://127.0.0.1:8888/](http://127.0.0.1:8888/)
        ProxyPassReverse / [http://127.0.0.1:8888/](http://127.0.0.1:8888/)

</VirtualHost>

- Now that the above is setup you will need to restart apache. 
- From here you will need to setup iptables so that no one can access the server by using the url and the port number. Iptables needs to set so that only 127.0.0.1 can access the port that gnump3d is running on.

The above configuration will also all authentication to work with gnump3d 3.0.

---

