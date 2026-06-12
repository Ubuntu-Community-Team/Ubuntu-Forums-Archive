---
title: "Adding Apache2 Modules"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Wangsta on 2008-06-19
I was wanting to add mod_auth_dbm module to Apache and still keep my current configuration.

Sorry for being a total noob, but how do I do that?:confused:

---

### Post by molotov00 on 2008-06-19
I'm unclear as to what you are trying to acheive. Please clarify.

[http://httpd.apache.org/docs/2.0/mod/mod_auth_dbm.html](http://httpd.apache.org/docs/2.0/mod/mod_auth_dbm.html)

---

### Post by Wangsta on 2008-06-23
So the auth_dbm module isn't enabled. How do I enable it without having to reconfigure everything?

---

### Post by Wangsta on 2008-06-23
bump

---

### Post by SpaceTeddy on 2008-06-24
```
sudo a2enmod mod_auth_dbm
sudo /etc/etc/init.d/apache2 force-reload
```

this will only enable the module - it will NOT do anything to your configuration. You will need to edit that afterwards to use the dbm module... 

hope it helps :)

---

### Post by Wangsta on 2008-06-24
Yay!
Thanks alot, this is exactly what i was looking for!:biggrin:

---

