---
title: "How do I: set this conf file right?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by TechDragon on 2010-05-27
I have a static ip and installed apache, I then installed drupal.  But I need a to know how to change the httpd.conf file so that when people type in my ipaddress that the apache webserver on my ubuntu box serves up the index page.  I have tried alot and could use a little assistance.

---

### Post by Ozymandias_117 on 2010-05-27
A quick work around until someone who knows more about apache... You can move your webpage to /var/www and it should show up.

---

### Post by aninaiian on 2010-05-28
I'm not much of an apache expert but if you'd want all directories on your site to have indexes without having to create index.html files you'd look for the line like this
```
<Directory />
    Options FollowSymLinks
    AllowOverride None
</Directory>

```

and change it to this 
```
<Directory />
    Options Indexes FollowSymLinks
    AllowOverride None
</Directory>

```

---

