---
title: "Apache stopped working after MySQL setup. Can't figure where to start fixing..."
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-08
Few days ago my apache was working and I could browse to localhost and view files I was creating while learning the php tutorial. But then the tutorial touched the topic of mysql, and I found that I had to setup mysql server. When I finally got my terminal show mysql> prompt and played with databases and tables a couple of moments I found that my apache no longer works. I deleteted all fifrefox cache and I couldn't even browse to localhost anymore. I don't know where to start fixing. I will provide all errors and logs if you need, but please help!

---

### Post by Ubunser on 2010-05-08
[HTML]proggist@proggist-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                      
Syntax error on line 9 of /etc/apache2/ports.conf:
Invalid address or port
                                                                         [fail]
[/HTML]

here's ports.conf content:
[HTML]# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen :80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>[/HTML]

error.log:
[HTML][Thu May 06 23:15:53 2010] [notice] caught SIGTERM, shutting down
[Thu May 06 23:21:44 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu May 06 23:58:19 2010] [notice] caught SIGTERM, shutting down
[Fri May 07 09:51:30 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri May 07 16:16:19 2010] [notice] caught SIGTERM, shutting down
[Fri May 07 16:41:14 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri May 07 16:49:00 2010] [error] [client ::1] File does not exist: /home/proggist/public_html/favicon.ico
[Fri May 07 16:49:03 2010] [error] [client ::1] File does not exist: /home/proggist/public_html/favicon.ico
[Fri May 07 17:40:57 2010] [notice] caught SIGTERM, shutting down
[Fri May 07 19:22:31 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri May 07 19:59:26 2010] [notice] caught SIGTERM, shutting down
[Fri May 07 19:59:27 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri May 07 20:37:22 2010] [notice] caught SIGTERM, shutting down
[Fri May 07 20:37:23 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri May 07 20:55:44 2010] [notice] caught SIGTERM, shutting down
[Fri May 07 21:06:01 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri May 07 22:04:58 2010] [notice] caught SIGTERM, shutting down[/HTML]

access.log:
[HTML]::1 - - [07/May/2010:16:49:00 +0300] "GET /favicon.ico HTTP/1.1" 404 262 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040116 Ubuntu/9.04 (jaunty) Firefox/3.0.19"
::1 - - [07/May/2010:16:49:03 +0300] "GET /welcome.php HTTP/1.1" 200 8161 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040116 Ubuntu/9.04 (jaunty) Firefox/3.0.19"
::1 - - [07/May/2010:16:49:03 +0300] "GET /welcome.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2524 "http://localhost/welcome.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040116 Ubuntu/9.04 (jaunty) Firefox/3.0.19"
::1 - - [07/May/2010:16:49:03 +0300] "GET /welcome.php?=SUHO8567F54-D428-14d2-A769-00DA302A5F18 HTTP/1.1" 200 2813 "http://localhost/welcome.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040116 Ubuntu/9.04 (jaunty) Firefox/3.0.19"
::1 - - [07/May/2010:16:49:03 +0300] "GET /welcome.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://localhost/welcome.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040116 Ubuntu/9.04 (jaunty) Firefox/3.0.19"
::1 - - [07/May/2010:16:49:03 +0300] "GET /favicon.ico HTTP/1.1" 404 262 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040116 Ubuntu/9.04 (jaunty) Firefox/3.0.19"[/HTML]

Maybe this will clear things out?

---

### Post by Jive Turkey on 2010-05-08
line 9 of your apache config is "Listen :80" try 0.0.0.0:80 or *:80, or put your actual IP, or localhost or something there, or just comment the line out with a "#" and restart apache.  It's really nice when applications tell you exactly where the problem is.  It's possible that if mod_ssl is called you'll get an error on the line that says "Listen :443"

Mine looks like this:```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

``` Look no colon!

---

### Post by Ubunser on 2010-05-08
> **Jive Turkey said:**
> line 9 of your apache config is "Listen :80" try 0.0.0.0:80 or *:80

When you were writing I just figured that and realized ":" was extra, so I removed it and the message about syntax error on line 9 dissappeared. But that's only I managed to undo the mistake I did trying to fix the original problem, which is by the way still remains unknown to me. 
So finally I now get this:
[HTML]proggist@proggist-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
[/HTML]

---

### Post by Ubunser on 2010-05-08
One manual advised to create a document .fqdn in conf.d with content: ServerName localhost. I did that and now in the terminal I get:
[HTML]proggist@proggist-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                 
 httpd (pid 9432) already running
                                                                         [ OK ]
[/HTML]
What does that mean?

And also after setting up MySQL I found that apache got back to using /var/www for default site "It Works!" Does it mean that it changed my document root? When I first installed apache I defined /home/public_html as my document root. So what's the importance of that?

---

### Post by Ubunser on 2010-05-08
Thank you guys! I just tried to access localhost and it works great! Thank you!

---

### Post by Jive Turkey on 2010-05-08
> **Ubunser said:**
> When you were writing I just figured that and realized ":" was extra, so I removed it and the message about syntax error on line 9 dissappeared. But that's only I managed to undo the mistake I did trying to fix the original problem, which is by the way still remains unknown to me. 
So finally I now get this:
[HTML]proggist@proggist-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
[/HTML]
The fdqn thing is a non-issue since you are only browsing localhost.

The "already running" message indicates just what it says, "sudo apache2ctl (restart or start or stop)" is a nice way to do that too.

---

