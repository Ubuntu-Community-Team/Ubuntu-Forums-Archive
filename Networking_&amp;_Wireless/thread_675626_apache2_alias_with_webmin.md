---
title: "apache2 alias with webmin"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by mhouston100 on 2008-01-22
Hi guys, first post :)

I'm sure i'm missing something very simple but here goes:

I have a website running on apache2 that I administer through webmin, this all runs great except for my site only responds to [http://host.site.com](http://host.site.com) and not [http://[B]WWW](http://[B]WWW)[/B.]host.site.com.  If I try and add any 'Alternate Virtual Server Names' through ( Virtual Server > Networking and Addresses > Alternate virtual server names) my whole server freezes, not just webmin, not just gnome, everything requiring a hard reboot.

I know that you can edit the individual conf files under /etc/apache2/available-sites but could someone help me with the syntax needed, I cant seem to find anything that works... here is my conf file:

```
<VirtualHost *>
DocumentRoot /www/b2evolution
<Directory "/www/b2evolution">
allow from all
Options +Indexes
UseCanonicalName off
</Directory>
ServerName host.site.com
UseCanonicalName off
</VirtualHost>
```

Under ServerName I have tried adding:

```
ServerAlias www.host.site.com
```

and even

```
*.host.site.com
```

but nothing seems to work properly...

Any help?

Thanks guys!

EDIT::

Just a thought, could this be because I use a dynamic DNS service, as in I only have host.site.com registered to forward to my IP, not **www**.host.site.com.  Maybe I need to set it up on the Dynamic DNS end.... hmmmm

---

