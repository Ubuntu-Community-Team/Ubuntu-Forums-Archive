---
title: "MySQL Database uninstall difficulties"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by LinuxConvert2010 on 2010-01-11
Hi,
Sorry if this may have been posted about before. I wasn't able to find it on the threads in this forum and I am very new to the whole Ubuntu/Linux game.

I completely buggered up my install of MySQL Server 5.1 having ever only done it on Windows and not being used to the easy style of Ubuntu installs. After a bit of difficulty, I found a way to get rid of MySQL and start again. I used the following command:

*sudo apt-get remove --purge mysql-server-5.1*

This seemed to work up until a certain point when it stopped working. I have included the transcript and bolded and underlined the area where the problem starts:

[I]sudo apt-get remove --purge mysql-server-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libhtml-template-perl libdbi-perl libdbd-mysql-perl
  mysql-client-5.1 libplrpc-perl mysql-server-core-5.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  mysql-server* mysql-server-5.1*
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
After this operation, 15.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164054 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.1 ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Purging configuration files for mysql-server-5.1 ...
_**dpkg: warning: while removing mysql-server-5.1, directory '/etc/mysql' not empty so not removed.**_
Processing triggers for man-db ...
Processing triggers for ureadahead ...[/I]




But  I removed everything in that directory myself. Has anyone encountered this and if so, what do you do as it seems to result in MySQL not being uninstalled? Also, please feel free to correct any etiquette errors I might have made.

Thank you!

---

### Post by cariboo on 2010-01-11
Are you sure the mysql server is stopped? The service has to be stop in order to completely uninstall it. Open a terminal and type:

```
sudo /etc/init.d/mysql stop
``` 

You should get something like this:

```
sudo /etc/init.d/mysql stop
[sudo] password for me:  
 * Stopping MySQL database server mysqld                                 [ OK ] 
```

In the above example I substituted me for my username. Once you have ensured that the service is stopped, you can then completely remove it.

---

