---
title: "apache authentication problem"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by ggaaron on 2007-06-18
This is my /etc/apache2/httpd.conf file. What I want to do is to is to have all files accessible, but not "pliki" folder. I can request authentication of whole server, but I can't do this to one folder=( I'm really starting with web servers.

```

<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
    AuthType Basic #if I delete this four lines, server will never ask me for password, I can access pliki folder without giving my user name and password.
    AuthName "Standard user and password: guest, guest"
    AuthUserFile /usr/local/apache/passwd/passwords
    Require valid-user
</Directory>

<Directory /pliki/>
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
    AuthType Basic
    AuthName "Standard user and password: guest, guest"
    AuthUserFile /usr/local/apache/passwd/passwords
    Require valid-user
</Directory>

```

---

