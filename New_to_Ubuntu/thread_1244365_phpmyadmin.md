---
title: "phpmyadmin"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Dev'olution on 2009-08-19
Hey,

I installed phpmyadmin via apt-get however it isn't even in /var/www :confused:

Any idea how i could get it to show up at [http://localhost/phpmyadmin](http://localhost/phpmyadmin) ???

---

### Post by kanikilu on 2009-08-19
I think by default it installs to /usr/share/phpmyadmin, and then sets up an alias called /phpmyadmin to it in the apache.conf in /etc/phpmyadmin.

The apache.conf is symlinked in /etc/apache2/conf.d as phpmyadmin.conf so that apache knows about the alias.

Have you restarted apache (sudo /etc/init.d/apache2 restart)? If all those files and links exist and are setup to create that alias, then the URL [http://localhost/phpmyadmin](http://localhost/phpmyadmin) should work...

---

