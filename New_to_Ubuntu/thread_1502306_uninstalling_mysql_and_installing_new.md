---
title: "uninstalling mysql and installing new"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by nvraja on 2010-06-05
I installed mysql server 5.1 earlier and after some time I forgot my root password, I tried to uninstall the old one and install a new, but got the following error ...

xxx@xxx:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
2 not fully installed or removed.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 172645 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.3_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nvraja on 2010-06-05
Got the following error while trying to install mysql:

raja@raja:~$ sudo apt-get install mysql-server-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
  mysql-server-5.1: Depends: mysql-client-5.1 (>= 5.1.31-1ubuntu2) but it is not going to be installed
                    Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
                    Recommends: mailx
                    Conflicts: mysql-server (< 5.1.31-1ubuntu2)
                    Conflicts: mysql-server-core-5.0 but 5.1.30really5.0.75-0ubuntu10.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)

---

### Post by nvraja on 2010-06-05
I've reset the password for Mysql server using
sudo dpkg-reconfigure mysql-server-5.1

---

