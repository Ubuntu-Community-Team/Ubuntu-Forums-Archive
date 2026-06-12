---
title: "Blocking Sub-Directories"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by pi3.1415926535... on 2011-04-04
Is it possible to block subdirectories? Say, block an individual page on a website? I know it is possible to block a domain from /etc/hosts.

Thank you

---

### Post by rosencrantz on 2011-04-04
Hi pi,
what exactly are going for? 
If you are running a HTML server like Apache, try this HowTo, especially the bit about the .htaccess file.
[http://httpd.apache.org/docs/current/howto/auth.html](http://httpd.apache.org/docs/current/howto/auth.html)
If you just want to set user access control for certain directories on your machine, create a group, add users, change the folder's group and check the permissions
sudo groupadd secretsociety
sudo usermod -g secretsociety rasputin 
sudo usermod -g secretsociety guyfawkes
sudo chgrp -R secretsociety secretfolder
sudo chmod -R 770 secretfolder (rwx access for users and group, no access for others, see [http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html) for more info)
Cheers,
rosencrantz

---

