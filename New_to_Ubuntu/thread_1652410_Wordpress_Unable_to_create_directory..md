---
title: "Wordpress Unable to create directory."
date: 2010-12-24
forum: New to Ubuntu
---

### Post by idavid on 2010-12-24
After trying to upload an image wp throwing this error.
Unable to create directory Is its parent directory writable by the server?
This is the tutorial that i follow to install my virtual server.

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#lamp](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#lamp)

Already try to change the path (wp) settings -> media -> Full URL path to files;

any thoughts?

---

### Post by idavid on 2010-12-25
bump

---

### Post by sandyd on 2010-12-25
> **idavid said:**
> After trying to upload an image wp throwing this error.
Unable to create directory Is its parent directory writable by the server?
This is the tutorial that i follow to install my virtual server.

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#lamp](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#lamp)

Already try to change the path (wp) settings -> media -> Full URL path to files;

any thoughts?
whats your apache username.

Is it apache2?

if it is...
```

sudo chown -R apache2:apache2 /var/www
```

the files/directories need to be owned by the same user as apache runs on

---

