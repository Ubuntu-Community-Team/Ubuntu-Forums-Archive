---
title: "mysql server"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by bjje on 2011-05-20
Synaptic seems to be bumpy today, when I try to download a package I get;

> E: mysql-server-5.1: subprocess installed post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured
details as below;


> Selecting previously deselected package banshee-extensions-common.
(Reading database ... 261685 files and directories currently installed.)
Unpacking banshee-extensions-common (from .../banshee-extensions-common_2.0.0-1ubuntu1_all.deb) ...
Selecting previously deselected package banshee-extension-radiostationfetcher.
Unpacking banshee-extension-radiostationfetcher (from .../banshee-extension-radiostationfetcher_2.0.0-1ubuntu1_all.deb) ...
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up banshee-extensions-common (2.0.0-1ubuntu1) ...
Setting up banshee-extension-radiostationfetcher (2.0.0-1ubuntu1) ...
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server

It prompts me to setup a passwd for mysql but won't complete the download. 

I tried to configure mysql at the terminal but no better.

It doesn't seem to be dependent on which packages I download. I have had no problems before with synaptic in natty.



??

---

### Post by jramshu on 2011-05-20
Dependencies can usually be resolved with apt-get dist-upgrade from terminal. The bad side is, 11.04 tends to want to remove pulseaudio. So if you go that way you need to watch carefully at what it tries to remove.

---

### Post by bjje on 2011-05-20
tried that, get the same prompt and message as below;

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

then it prompt me for bug report.

Hmmm...

---

### Post by jramshu on 2011-05-20
Have you tried 
```
sudo apt-get install -f
```

EDIT: Been looking around and found some others with the same problem. It looks like it never finished installing correctly. May have to reinstall it.

---

### Post by bjje on 2011-05-20
yes and I get;
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                           Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jramshu on 2011-05-20
I found this, might help. 

[http://serverfault.com/questions/254629/unable-to-install-mysql-server-in-ubuntu](http://serverfault.com/questions/254629/unable-to-install-mysql-server-in-ubuntu)

---

### Post by webofunni on 2011-05-20
first try to findout why the mysql server start fails or why dpkg returns that error. what is the output of service mysql start ? 

check the mysql server logs also, if available.

---

### Post by jramshu on 2011-05-20
From what I have been reading it's a file permission problem.

One person having this problem just did this and his started working.
```
sudo apt-get install mysql-server-5.1
```

---

### Post by bjje on 2011-05-20
Nope, same thing;
> 
 sudo apt-get install mysql-server-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                           Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bjje on 2011-05-20
sudo service mysql start
start: Job failed to start

---

### Post by jramshu on 2011-05-20
You need to look in the logs and see exactly why its failing.

Should be in "/var/log/mysql/error.log" or something similar.

---

### Post by webofunni on 2011-05-20
> **bjje said:**
> sudo service mysql start
start: Job failed to start
That is not giving much details try 

```
sudo /etc/init.d/mysql start
```

also post the mysql error log entries.

---

### Post by bjje on 2011-05-23
```


sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job failed to start
$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.79" (uid=1000 pid=10045 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```/var/log/mysql$ 

```
110523  9:05:30 [Note] Plugin 'FEDERATED' is disabled.
110523  9:05:30  InnoDB: Initializing buffer pool, size = 8.0M
110523  9:05:30  InnoDB: Completed initialization of buffer pool
110523  9:05:30  InnoDB: Started; log sequence number 0 44233
110523  9:05:31  InnoDB: Starting shutdown...
110523  9:05:36  InnoDB: Shutdown completed; log sequence number 0 44233
110523  9:05:36 [Note] Plugin 'FEDERATED' is disabled.
110523  9:05:36  InnoDB: Initializing buffer pool, size = 8.0M
110523  9:05:36  InnoDB: Completed initialization of buffer pool
110523  9:05:36  InnoDB: Started; log sequence number 0 44233
ERROR: 1050  Table 'plugin' already exists
110523  9:05:36 [ERROR] Aborting

110523  9:05:36  InnoDB: Starting shutdown...
110523  9:05:41  InnoDB: Shutdown completed; log sequence number 0 44233
110523  9:05:41 [Note] /usr/sbin/mysqld: Shutdown complete

```

---

### Post by webofunni on 2011-05-23
If this is a new mysql installation try this 

```
sudo dpkg -P mysql-server-5.1 mysql-server
sudo apt-get install mysql-server
```

Let me know, if the error persists.

---

### Post by bjje on 2011-05-23
dpkg runs but;

> sudo apt-get install mysql-server

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by webofunni on 2011-05-23
ok, execute following commands and also paste the result of each of them. 

```

sudo dpkg -P mysql-server mysql-server-5.1
sudo apt-get autoremove
sudo apt-get clean
dpkg -l | grep -i mysql
sudo rm -rvf /var/lib/mysql
sudo apt-get install mysql-server

```

Again, I am assuming that this is a new mysql installation with no database created.

---

### Post by bjje on 2011-05-23
It's new only to the extent that I have previously removed it trying to fix this. Remember that my problem happened in the middle of installing some packages and it broke my ability to install any or update.  Thanks,

```
sudo dpkg -P mysql-server mysql-server-5.1
(Reading database ... 262011 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.1 ...
Purging configuration files for mysql-server-5.1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
 sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo apt-get clean
 dpkg -l | grep -i mysql
ii  libdbd-mysql-perl                     4.016-1                                    Perl5 database interface to the MySQL database
ii  libmysqlclient16                      5.1.54-1ubuntu4                            MySQL database client library
ii  libqt4-sql-mysql                      4:4.7.2-0ubuntu6.1                         Qt 4 MySQL database driver
ii  mysql-client-5.1                      5.1.54-1ubuntu4                            MySQL database client binaries
ii  mysql-client-core-5.1                 5.1.54-1ubuntu4                            MySQL database core client binaries
ii  mysql-common                          5.1.54-1ubuntu4                            MySQL database common files, e.g. /etc/mysql/my.cnf
ii  mysql-server-core-5.1                 5.1.54-1ubuntu4                            MySQL database server binaries
ii  php5-mysql                            5.3.5-1ubuntu7.2                           MySQL module for php5
ii  python-mysqldb                        1.2.2-10build2                             A Python interface to MySQL
sudo rm -rvf /var/lib/mysql
removed `/var/lib/mysql/debian-5.1.flag'
removed `/var/lib/mysql/mysql/help_relation.MYI'
removed `/var/lib/mysql/mysql/time_zone_leap_second.MYI'
removed `/var/lib/mysql/mysql/help_category.frm'
removed `/var/lib/mysql/mysql/tables_priv.MYI'
removed `/var/lib/mysql/mysql/user.MYI'
removed `/var/lib/mysql/mysql/time_zone_name.frm'
removed `/var/lib/mysql/mysql/help_topic.MYI'
removed `/var/lib/mysql/mysql/host.frm'
removed `/var/lib/mysql/mysql/slow_log.frm'
removed `/var/lib/mysql/mysql/time_zone_leap_second.frm'
removed `/var/lib/mysql/mysql/db.MYD'
removed `/var/lib/mysql/mysql/procs_priv.MYD'
removed `/var/lib/mysql/mysql/plugin.frm'
removed `/var/lib/mysql/mysql/time_zone.frm'
removed `/var/lib/mysql/mysql/time_zone_transition_type.frm'
removed `/var/lib/mysql/mysql/user.frm'
removed `/var/lib/mysql/mysql/time_zone_transition_type.MYD'
removed `/var/lib/mysql/mysql/columns_priv.MYI'
removed `/var/lib/mysql/mysql/proc.MYD'
removed `/var/lib/mysql/mysql/ndb_binlog_index.MYI'
removed `/var/lib/mysql/mysql/general_log.frm'
removed `/var/lib/mysql/mysql/help_keyword.MYD'
removed `/var/lib/mysql/mysql/tables_priv.frm'
removed `/var/lib/mysql/mysql/time_zone.MYI'
removed `/var/lib/mysql/mysql/help_topic.MYD'
removed `/var/lib/mysql/mysql/help_relation.MYD'
removed `/var/lib/mysql/mysql/time_zone_leap_second.MYD'
removed `/var/lib/mysql/mysql/db.frm'
removed `/var/lib/mysql/mysql/help_topic.frm'
removed `/var/lib/mysql/mysql/servers.MYI'
removed `/var/lib/mysql/mysql/host.MYI'
removed `/var/lib/mysql/mysql/host.MYD'
removed `/var/lib/mysql/mysql/time_zone.MYD'
removed `/var/lib/mysql/mysql/user.MYD'
removed `/var/lib/mysql/mysql/proc.MYI'
removed `/var/lib/mysql/mysql/slow_log.CSV'
removed `/var/lib/mysql/mysql/event.frm'
removed `/var/lib/mysql/mysql/columns_priv.frm'
removed `/var/lib/mysql/mysql/servers.MYD'
removed `/var/lib/mysql/mysql/tables_priv.MYD'
removed `/var/lib/mysql/mysql/time_zone_transition.MYI'
removed `/var/lib/mysql/mysql/ndb_binlog_index.frm'
removed `/var/lib/mysql/mysql/general_log.CSM'
removed `/var/lib/mysql/mysql/time_zone_name.MYI'
removed `/var/lib/mysql/mysql/plugin.MYI'
removed `/var/lib/mysql/mysql/ndb_binlog_index.MYD'
removed `/var/lib/mysql/mysql/columns_priv.MYD'
removed `/var/lib/mysql/mysql/help_keyword.frm'
removed `/var/lib/mysql/mysql/time_zone_transition_type.MYI'
removed `/var/lib/mysql/mysql/slow_log.CSM'
removed `/var/lib/mysql/mysql/db.MYI'
removed `/var/lib/mysql/mysql/procs_priv.MYI'
removed `/var/lib/mysql/mysql/time_zone_transition.frm'
removed `/var/lib/mysql/mysql/general_log.CSV'
removed `/var/lib/mysql/mysql/time_zone_name.MYD'
removed `/var/lib/mysql/mysql/servers.frm'
removed `/var/lib/mysql/mysql/help_category.MYD'
removed `/var/lib/mysql/mysql/proc.frm'
removed `/var/lib/mysql/mysql/plugin.MYD'
removed `/var/lib/mysql/mysql/event.MYD'
removed `/var/lib/mysql/mysql/event.MYI'
removed `/var/lib/mysql/mysql/func.MYD'
removed `/var/lib/mysql/mysql/help_category.MYI'
removed `/var/lib/mysql/mysql/help_relation.frm'
removed `/var/lib/mysql/mysql/func.frm'
removed `/var/lib/mysql/mysql/help_keyword.MYI'
removed `/var/lib/mysql/mysql/time_zone_transition.MYD'
removed `/var/lib/mysql/mysql/procs_priv.frm'
removed `/var/lib/mysql/mysql/func.MYI'
removed directory: `/var/lib/mysql/mysql'
removed `/var/lib/mysql/ibdata1'
removed `/var/lib/mysql/ib_logfile0'
removed `/var/lib/mysql/ib_logfile1'
removed directory: `/var/lib/mysql'
 sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.1
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,265 kB of archives.
After this operation, 13.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main mysql-server-5.1 i386 5.1.54-1ubuntu4 [6,258 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main mysql-server all 5.1.54-1ubuntu4 [6,828 B]
Fetched 6,265 kB in 4s (1,398 kB/s)
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 261932 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by webofunni on 2011-05-24
It seems autoremove is not removing the dep. try

```

sudo dpkg -P mysql-server mysql-server-5.1 mysql-common mysql-server-core-5.1 php5-mysql mysql-client-5.1 mysql-client-core-5.1
sudo apt-get install mysql-server

```

paste the result of above commands and result of logs, if the issue persists. 

```

sudo start mysql;sudo tail -20 /var/log/mysql/error.log

```

---

### Post by bjje on 2011-05-24
Same old thing'
```

sudo dpkg -P mysql-server mysql-server-5.1 mysql-common mysql-server-core-5.1 php5-mysql mysql-client-5.1 mysql-client-core-5.1
dpkg: warning: there's no installed package matching mysql-server
dpkg: warning: there's no installed package matching mysql-server-5.1
dpkg: warning: there's no installed package matching php5-mysql
dpkg: dependency problems prevent removal of mysql-common:
 libmysqlclient16 depends on mysql-common (>= 5.1.54-1ubuntu4).
dpkg: error processing mysql-common (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of mysql-server-core-5.1:
 akonadi-server depends on mysql-server-core-5.1.
dpkg: error processing mysql-server-core-5.1 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of mysql-client-5.1:
 mythtv-common depends on mysql-client; however:
  Package mysql-client is not installed.
  Package mysql-client-5.1 which provides mysql-client is to be removed.
dpkg: error processing mysql-client-5.1 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of mysql-client-core-5.1:
 mysql-client-5.1 depends on mysql-client-core-5.1.
 akonadi-server depends on mysql-client-core-5.1.
dpkg: error processing mysql-client-core-5.1 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 mysql-common
 mysql-server-core-5.1
 mysql-client-5.1
 mysql-client-core-5.1

```

---

### Post by bjje on 2011-05-24
```
 sudo start mysql;sudo tail -20 /var/log/mysql/error.log
start: Job failed to start
110524 13:24:28  InnoDB: Shutdown completed; log sequence number 0 44233
110524 13:24:28 [Note] /usr/sbin/mysqld: Shutdown complete

110524 13:24:28 [Note] Plugin 'FEDERATED' is disabled.
110524 13:24:28  InnoDB: Initializing buffer pool, size = 8.0M
110524 13:24:28  InnoDB: Completed initialization of buffer pool
110524 13:24:28  InnoDB: Started; log sequence number 0 44233
110524 13:24:28  InnoDB: Starting shutdown...
110524 13:24:33  InnoDB: Shutdown completed; log sequence number 0 44233
110524 13:24:33 [Note] Plugin 'FEDERATED' is disabled.
110524 13:24:33  InnoDB: Initializing buffer pool, size = 8.0M
110524 13:24:33  InnoDB: Completed initialization of buffer pool
110524 13:24:33  InnoDB: Started; log sequence number 0 44233
ERROR: 1050  Table 'plugin' already exists
110524 13:24:33 [ERROR] Aborting

110524 13:24:33  InnoDB: Starting shutdown...
110524 13:24:39  InnoDB: Shutdown completed; log sequence number 0 44233
110524 13:24:39 [Note] /usr/sbin/mysqld: Shutdown complete

```

---

### Post by webofunni on 2011-05-24
Sad to hear that :-( .what 

```

sudo dpkg -P --force depends mysql-server mysql-server-5.1 mysql-common mysql-server-core-5.1 php5-mysql mysql-client-5.1 mysql-client-core-5.1

```

says ? 

Do the following, if that successful and paste the result. 

```

sudo apt-get install mysql-server
sudo start mysql;sudo tail -20 /var/log/mysql/error.log

```

---

### Post by webofunni on 2011-05-24
are you using KDE or Gnome ? akonadi-server package usually comes with KDE.

---

### Post by webofunni on 2011-05-24
You can also try 

```

apt-get

```

if dpkg fails again

---

### Post by bjje on 2011-05-24
That did it!  I then could remove akondai which fixed the problem. I use gnome. I must have been downloading akondai by a mistaken mouse click but I still don't understand why that was as far reaching as it turned out. I am truly an absolute beginner but I'll work on it.
Many thankyoos for your persistance
BJJE


```

 sudo dpkg -P --force depends mysql-server mysql-server-5.1 mysql-common mysql-server-core-5.1 php5-mysql mysql-client-5.1 mysql-client-core-5.1

dpkg: warning: there's no installed package matching php5-mysql
(Reading database ... 262207 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.1 ...
Purging configuration files for mysql-server-5.1 ...
dpkg: mysql-client-5.1: dependency problems, but removing anyway as you requested:
 mythtv-common depends on mysql-client; however:
  Package mysql-client is not installed.
  Package mysql-client-5.1 which provides mysql-client is to be removed.
Removing mysql-client-5.1 ...
dpkg: mysql-client-core-5.1: dependency problems, but removing anyway as you requested:
 akonadi-server depends on mysql-client-core-5.1.
Removing mysql-client-core-5.1 ...
dpkg: mysql-common: dependency problems, but removing anyway as you requested:
 libmysqlclient16 depends on mysql-common (>= 5.1.54-1ubuntu4).
Removing mysql-common ...
Purging configuration files for mysql-common ...
dpkg: warning: while removing mysql-common, directory '/etc/mysql' not empty so not removed.
dpkg: mysql-server-core-5.1: dependency problems, but removing anyway as you requested:
 akonadi-server depends on mysql-server-core-5.1.
Removing mysql-server-core-5.1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...

```

---

### Post by webofunni on 2011-05-24
You might have installed any Qt based application

[http://en.wikipedia.org/wiki/Qt_%28framework%29](http://en.wikipedia.org/wiki/Qt_%28framework%29)

Are you able to install and start Mysql server now ? 

Glad to hear things started working :-)

---

### Post by bjje on 2011-05-25
Well, no. I guess I have some reading to do.
I get the same result as before;

 ```
sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.1
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.1
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/6,265 kB of archives.
After this operation, 13.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 260368 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```but at least my dpkg works again:)

BJ

---

### Post by webofunni on 2011-05-25
You said everything working correct. Was this working before ?

---

### Post by bjje on 2011-05-25
No, but I hadn't reinstalled it yet. I don't think I need it for anything but it won't install properly.

---

### Post by vidtek on 2011-07-17
If this helps anyone, this sorted mine out (Ultimate edition 2.9 10.10):

Not too sure about the 500+ GB at the end though!

```
tony@workshopubuntu:~$ sudo aptitude install -f
The following NEW packages will be installed:
  gtk2-engines-mythbuntu mythbuntu-lirc-generator{b} mythexport{b} 
  ultimate-edition-themes 
The following partially installed packages will be configured:
  mysql-server mysql-server-5.1 mythtv 
0 packages upgraded, 4 newly installed, 0 to remove and 2006 not upgraded.
Need to get 410MB of archives. After unpacking 591GB will be used.
The following packages have unmet dependencies:
  mythexport: Depends: atomicparsley but it is not going to be installed.
              Depends: libconfig-simple-perl but it is not going to be installed.
              Depends: libproc-daemon-perl but it is not going to be installed.
              Depends: libproc-pid-file-perl but it is not going to be installed.
              Depends: liblog-dispatch-perl but it is not going to be installed.
  mythbuntu-lirc-generator: Depends: python (>= 2.7) but 2.6.6-2ubuntu2 is installed and it is kept back.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     mythbuntu-lirc-generator [Not Installed]           
2)     mythexport [Not Installed]                         



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  gtk2-engines-mythbuntu ultimate-edition-themes 
The following partially installed packages will be configured:
  mysql-server mysql-server-5.1 mythtv 
0 packages upgraded, 2 newly installed, 0 to remove and 2006 not upgraded.
Need to get 410MB of archives. After unpacking 591GB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://ftp.iinet.net.au/pub/ubuntu/ natty/universe gtk2-engines-mythbuntu all 0.4-0ubuntu2 [44.2kB]
Get:2 http://themelinux.com/themes/ themes/all ultimate-edition-themes all 0.1.1 [410MB]
2% [2 ultimate-edition-themes 9573448/410MB 2%]                                    132kB/s 50min 40sony@workshopubuntu:~$ sudo aptitude install -f                                                      
The following NEW packages will be installed:                                                       
  gtk2-engines-mythbuntu mythbuntu-lirc-generator{b} mythexport{b}                                  
  ultimate-edition-themes                                                                           
The following partially installed packages will be configured:                                      
  mysql-server mysql-server-5.1 mythtv                                                              
0 packages upgraded, 4 newly installed, 0 to remove and 2006 not upgraded.                          
Need to get 410MB of archives. After unpacking 591GB will be used.                                  
3% [2 ultimate-edition-themes 15834472/410MB 3%]  


```

---

### Post by bjje on 2011-07-18
Thank you but I ended up doing a fresh install. I had a few other lurking problems so I just bit the bullet although I really like to upgrade instead. I figure that the more practice I get hunting down glitches, so much the better.

---

### Post by Nathan.zhu on 2012-01-16
Thanks, webofunni

I follow your step solved problem on mysql, thank you very much. ?

don't need fresh install system.

---

### Post by F1R3F7Y on 2012-06-27
I had this fault on Debian Squeeze.

The error in the syslog pointed to loopback device not enabled so mysql could not bind to 127.0.0.1 - localhost . brought up the lo device and it installedd correctly.

D

---

### Post by oldos2er on 2012-06-27
Old thread closed.

---

