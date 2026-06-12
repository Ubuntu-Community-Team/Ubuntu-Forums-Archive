---
title: "How do I start MySQL database"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by bwallum on 2010-02-02
Hi

I have done something to a MySQL database and mis configured it. I thought I had deleted MySQL and re-installed. However when trying to re-install using```
sudo apt-get install mysql-server
```I get this message> Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
The following packages were automatically installed and are no longer required:
  libqscintilla2-5 libgtkhtml3.8-15 exim4-daemon-light exim4-config bsd-mailx
  exim4 exim4-base mailx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.37-1ubuntu5) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)Can anybody help me move forward?

---

### Post by zwaardmeester on 2010-02-02
It looks like there are dependencies missing. Try to reinstall the package:
```
sudo apt-get remove mysql-server
```
then
```
sudo apt-get install mysql-server
```

If that does not help, try the same commands with mysql-server-5.1 instead of mysql-server.

---

### Post by bwallum on 2010-02-07
Apologies for the delay, I've been round the houses but finally got there.

My initial problem may have been loading the wrong version of MySQL Workbench.

To resolve I completely removed all mysql files. I found that I had to remove mysql-server-5.1 first, then mysql-server then mysql-client. This blew up OpenOffice. So I removed OOo and reinstalled that. The re-installation had the effect of stripping out the [Ubuntu colour theme]("http://ubuntuforums.org/showthread.php?t=1398885"), so I reinstalled it.

I then```
sudo apt-get install mysql-server-5.1 mysql-client
```then loaded the latest [MySQL Workbench]("http://wb.mysql.com/") which in my case happened to be version 5.2.15 beta5.

All now working, my databases are all still there and I can access them freely!

Thank you very much for the steer.

---

