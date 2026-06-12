---
title: "Problem installing torrentflux-b4rt"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by FireFreek on 2010-08-16
Every guide on installing torrentflux-b4rt in ubuntu server says the same step that i can't get past. I'm using ubuntu server 8.10. While using the setup.php, it asks for the details of the database, and guides tell you to go to [http://[your](http://[your) ip]/phpmyadmin. But there's nothing there. There's no phpmyadmin folder in /var/www.

I'm following this guide: [http://ubuntuforums.org/showthread.php?t=848138](http://ubuntuforums.org/showthread.php?t=848138)

can someone help me

EDIT: I fixed it by linking the phpmyadmin folder from /usr/share to /var/www. However, i cannot login to phpmyadmin. What user and pass do i use.

---

### Post by sandyd on 2010-08-16
> **FireFreek said:**
> Every guide on installing torrentflux-b4rt in ubuntu server says the same step that i can't get past. I'm using ubuntu server 8.10. While using the setup.php, it asks for the details of the database, and guides tell you to go to [http://](http://)[your ip]/phpmyadmin. But there's nothing there. There's no phpmyadmin folder in /var/www.

I'm following this guide: [http://ubuntuforums.org/showthread.php?t=848138](http://ubuntuforums.org/showthread.php?t=848138)

can someone help me

EDIT: I fixed it by linking the phpmyadmin folder from /usr/share to /var/www. However, i cannot login to phpmyadmin. What user and pass do i use.
your mysql root password.
you set that during the installation of mysql.

if you really don't remember setting it, check if mysql-server is installed or not
if its already installed... -> [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)

---

### Post by FireFreek on 2010-08-16
Well, i checked if it was installed by running sudo apt-get install mysql-server, but that updated it. And now i can't get it running. Can you tell me how i can uninstall then reinstall a lamp server(i set it during server install). Also before i do all that would saying

sudo apt-get remove php5-cli php5-gd libxml-dom-perl libxml-simple-perl libthreads-shared-perl libdigest-sha1-perl libhtml-parser-perl zip unzip unrar transmission-cli phpmyadmin

be acceptable to remove anything i installed trying to get it working?

---

### Post by FireFreek on 2010-08-16
OK I did all that i said i did in the last post, but now whenever i try and login to the phpmyadmin page, every time it asks me to download index.php

I deleted the symlink from /var/www/phpmyadmin to  /usr/share/phpmyadmin. Now i'm back to the problem where i can't access the phpmyadmin page.

EDIT: It seems i can't view any .php files. I think my php didn't install.

---

