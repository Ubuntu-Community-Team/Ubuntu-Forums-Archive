---
title: "Pear Install"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by darkstar_dev on 2010-07-12
If I install PEAR onto a Linux Server for Drupal Development, will it have any consequences on a LAMP or SAMBA server besides having to restart the server? I would like to install and have as little down time of the sites as possible, how will this affect the server?

If someone could help me I would really appreciate it!

Thanks

---

### Post by cariboo on 2010-07-12
The P in LAMP stands for php, so you won't have a problem with pear. 

BTW you never have to restart your server after installing packages, just restart the service, in this case just restart apache, if it isn't restarted when pear is installed.

---

