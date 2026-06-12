---
title: "Problems with MySQL"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by GhostBear on 2007-09-06
Hi guys, I'm trying to set up a LAMP server on my system, running 7.04.

It seems to be having problems starting the MySQL server. eg

I try the following install command:

sudo apt-get install mysql-server

which gives:

> 
root@ady-laptop:/home/ady# sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/47.5kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Selecting previously deselected package mysql-server.
(Reading database ... 110744 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
 * Stopping MySQL database server mysqld                                                [ OK ] 
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                                [ OK ] 
 * Starting MySQL database server mysqld                                                [COLOR="Red"][fail][/COLOR] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


Following various how-to's I tried to purge the installed MySQL stuff to install from scratch thus:

sudo apt-get remove --purge mysql-server

which gives:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  mysql-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110746 files and directories currently installed.)
Removing mysql-server ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                                [ OK ] 
 * Starting MySQL database server mysqld                                                [COLOR="Red"][fail][/COLOR] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ady-laptop:/home/ady# 


Does anyone have any idea whats gone wrong, and how to fix it??

---

### Post by karvec on 2007-09-06
I do not have much experience with this, but what are you using?

LAMPP from apache friends?

Because that would install everything you need in WWW and then you could go from there...

---

