---
title: "hosts.deny file not working as expected"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2007-05-23
I"m trying to generate a hosts.deny file in /etc/hosts.deny but it isn't behaving as expected


The Contents:

httpd:ALL EXCEPT 127.0.0.1:DENY

and that's it.

I'm running Fiesty Fawn.

I've also tried www and 80 in the httpd field, to no effect, I'm able to get to the web server remotely, which is what I don't want.

---

### Post by chenel on 2008-01-10
You can't do it with hosts.deny unless you want to run apache through (x)inetd.

Check out [this page]("http://unixresources.org/linux/lf/57/archive/00/00/05/64/56451.html") for more information


What you should do instead is do this configuration through Apache:
open up your /etc/apache2/httpd.conf and add a section (assuming your web root is /var/www) and insert
```

<Directory "/var/www/">
     Order Deny,Allow
     Deny from all
     Allow from 127.0.0.1
</Directory>
```

see the [apache documentation]("http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html") for more info.
     

-chenel

> **mohnkern said:**
> I"m trying to generate a hosts.deny file in /etc/hosts.deny but it isn't behaving as expected


The Contents:

httpd:ALL EXCEPT 127.0.0.1:DENY

and that's it.

I'm running Fiesty Fawn.

I've also tried www and 80 in the httpd field, to no effect, I'm able to get to the web server remotely, which is what I don't want.

---

