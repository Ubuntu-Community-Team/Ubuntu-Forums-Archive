---
title: "apache"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by redmansk8 on 2008-06-27
Hello! I want to make sure I'm on the right path I have a static IP address at my office. I have a Ubuntu computer running apache2 webserver and I have 5 domain names. If I want my Ubuntu computer to host my five domain names. I need to create directories for each one in the /var/www directory. Then edit the httpd.conf file with something like this NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.domain.tld](www.domain.tld)
ServerAlias domain.tld *.domain.tld
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
ServerName [www.otherdomain.tld](www.otherdomain.tld)
DocumentRoot /www/otherdomain
</VirtualHost>
then all I do is point my domain names to my static IP address.
I'm I on the right path?

---

### Post by plewisfdx on 2008-06-27
I think this line

```
DocumentRoot /www/domain
```

should be this:

```
DocumentRoot /var/www/domain
```

The rest looks good, I think.

---

### Post by redmansk8 on 2008-06-27
Thanks You are right. It is /var/www

---

