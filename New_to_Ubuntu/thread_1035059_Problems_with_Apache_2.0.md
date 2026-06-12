---
title: "Problems with Apache 2.0"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by mojo_man on 2009-01-09
Hi,

I am running Apache 2.0 on my Ubuntu 8.04. When I put DocumentRoot setting in my apach2.conf and restart the apach2 daemon, apache does not seem to serve the pages from where I specify. Apach.conf report no errors when the Daemon is started so I am confused. 

Any suggestions?

---

### Post by spiderbatdad on 2009-01-09
If you see the "It Works" index.html, this file is kept in /var/www, as specified in the file /etc/apache2/sites-available/default...have a look at that file. Copy it to a file called "mysite" or anything you like. Then edit mysite to point to the DocumentRoot you choose. Disable the default site and enable mysite with ```
sudo a2dissite default && sudo a2ensite mysite
```

---

### Post by jken146 on 2009-01-09
> **spiderbatdad said:**
> If you see the "It Works" index.html, this file is kept in /var/www, as specified in the file /etc/apache2/sites-available/default...have a look at that file. Copy it to a file called "mysite" or anything you like. Then edit mysite to point to the DocumentRoot you choose. Disable the default site and enable mysite with ```
sudo a2dissite default && sudo a2ensite mysite
```

See also: [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

---

