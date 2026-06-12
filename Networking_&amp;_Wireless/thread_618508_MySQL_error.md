---
title: "MySQL error"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by ixlam on 2007-11-20
I'm using Gusty 7.1 on an x86 athlon machine 

I installed LAMP but now I cannot use synaptic or Apache.
Synaptic suggests  i run dpkg --configure -a

but I get this error >>>

:~$ sudo dpkg --configure -a

Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

I originally just wanted to set up Apache to host my site..
can n e one  help please ?

---

