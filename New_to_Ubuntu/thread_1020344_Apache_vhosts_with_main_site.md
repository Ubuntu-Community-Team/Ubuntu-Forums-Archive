---
title: "Apache vhosts with main site"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by JustYakov on 2008-12-24
Hello everyone!

I'd like to know how can I make a vhost of a subdomain to redirect to a page, but everything else (main site, local hostname, IP, localhost, etc.) to be redirected to the main site.

Here's a "rough draft" of what I want:
```
DocumentRoot /var/www

NameVirtualHost *
<VirtualHost *>
ServerName sub.mysite.com
DocumentRoot /home/sub
</VirtualHost>
```

So, if I go to sub.mysite.com I want to be redirected to /home/sub, but if I request mysite.com or localhost I want to be redirected to /var/www. Is there a good way?

Thanks in advance!

---

### Post by superprash2003 on 2008-12-24
hope this helps [http://apptools.com/phptools/virtualhost.php](http://apptools.com/phptools/virtualhost.php)


merry christmas..

---

