---
title: "mysql"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by rhengeh on 2010-07-26
super users - I need your help in getting MySQL running.  See script below for more info.  It appears to me that i've got server and client, but I'm unable to confirm that its running.    Please advise.




rgh66@rgh66-laptop:~$ sudo apt-get install mysql-server mysql-client
[sudo] password for rgh66: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
The following NEW packages will be installed:
  mysql-client
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 93.3kB of archives.
After this operation, 131kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main mysql-client 5.1.41-3ubuntu12.3 [93.3kB]
Fetched 93.3kB in 0s (107kB/s)        
Selecting previously deselected package mysql-client.
(Reading database ... 134421 files and directories currently installed.)
Unpacking mysql-client (from .../mysql-client_5.1.41-3ubuntu12.3_all.deb) ...
Setting up mysql-client (5.1.41-3ubuntu12.3) ...
rgh66@rgh66-laptop:~$ sudo netstat -tap | grep mysql
rgh66@rgh66-laptop:~$ sudo /etc/init.d/mysql restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mysql

Warning: Fake initctl called, doing nothing.
rgh66@rgh66-laptop:~$ sudo netstat -tap | grep mysql
rgh66@rgh66-laptop:~$ sudo mysqladmin -u root password newrootsqlpassword
mysqladmin: connect to server at 'localhost' failed[/B]
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
rgh66@rgh66-laptop:~$ mysql-server help
mysql-server: command not found
rgh66@rgh66-laptop:~$ sudo mysql-server help
sudo: mysql-server: command not found
rgh66@rgh66-laptop:~$ sudo mysqladmin -u root -h localhost password newrootsqlpassword
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
rgh66@rgh66-laptop:~$ sudo service restart mysql
restart: unrecognized service
rgh66@rgh66-laptop:~$ sudo service mysql restart

Warning: Fake initctl called, doing nothing.
rgh66@rgh66-laptop:~$

---

### Post by cariboo on 2010-07-26
From synaptic package manager:

> This is an empty package that depends on the current "best" version of
mysql-server (currently mysql-server-5.1), as determined by the MySQL
maintainers. Install this package if in doubt about which MySQL
version you need. That will install the version recommended by the
package maintainers.

you need to make sure that mysql-server-5.1 is installed, then start it using the following command:

```
sudo service mysql-server-5.1 start
```

---

