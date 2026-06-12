---
title: "Apache2 Change Port from 443"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-16
Hi all,

I want to change my https site from port 443 to 80 as the default port. Googled and have found the file ports.conf I set it up to look like this:
```
NameVirtualHost *:80
Listen 79

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 80
</IfModule>

```

I have changed the references to the ports in sites-available too, but I get this:
```
Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

    Hint: https://localhost.localdomain:80/

Apache/2.2.16 (Ubuntu) Server at localhost.localdomain Port 80
```
[https://host](https://host) returns "The connection was reset" etc. 

How do I fix this please?

Thanks!

---

### Post by Chrissd on 2011-05-16
Woohoo, fixed!

How stupid of me, just needed to go to [https://host:80](https://host:80)

Thanks!

---

