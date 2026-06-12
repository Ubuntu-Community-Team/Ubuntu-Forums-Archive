---
title: "MythTV (cannot connect to backend)"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by somuchfortheafter on 2008-04-04
I have a mythtv system connected to my tv currently and works fine it is its own frontend and backend. I just purchased an EEE PC and loaded 2gb of ram into it and installed eeeXubuntu. Then I installed mythtv, a few themes, and mythtv-front end. I then edited /etc/mythtv/mysql.txt to be the exact same as my working machine except for the hostname which I changed to the IP address of the box. Now I get the following errors when I try to connect with mythtv frontend.
```

chris@eeepc:~$ mythfrontend
2008-04-04 17:05:07.251 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-04 17:05:08.015 XScreenSaver support enabled
2008-04-04 17:05:08.016 DPMS is active.
2008-04-04 17:05:08.017 Empty LocalHostName.
2008-04-04 17:05:08.018 Using localhost value of eeepc
2008-04-04 17:05:08.071 New DB connection, total: 1
2008-04-04 17:05:08.109 Connected to database 'mythconverg' at host: 192.168.11.16
2008-04-04 17:05:08.114 Closing DB connection named 'DBManager0'
2008-04-04 17:05:08.115 Total desktop dim: 800x480, with 1 screen[s].
2008-04-04 17:05:08.119 Connected to database 'mythconverg' at host: 192.168.11.16
2008-04-04 17:05:08.127 Using screen 0, 800x480 at 0,0
2008-04-04 17:05:08.197 New DB connection, total: 2
2008-04-04 17:05:08.201 Connected to database 'mythconverg' at host: 192.168.11.16
2008-04-04 17:05:08.208 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-04-04 17:05:08.211 Enabled verbose msgs:  important general
2008-04-04 17:05:09.640 Total desktop dim: 800x480, with 1 screen[s].
2008-04-04 17:05:09.643 Using screen 0, 800x480 at 0,0
2008-04-04 17:05:09.647 Switching to square mode (MythCenter)
2008-04-04 17:05:09.702 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-04-04 17:05:09.706 lirc_init failed for mythtv, see preceding messages
2008-04-04 17:05:09.707 JoystickMenuClient Error: Joystick disabled - Failed to read /home/chris/.mythtv/joystickmenurc
2008-04-04 17:05:10.444 Loading from: /usr/share/mythtv/themes/MythCenter/base.xml
2008-04-04 17:05:10.648 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-04 17:05:10.983 Registering Internal as a media playback plugin.
2008-04-04 17:05:14.340 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-04 17:05:14.341 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2008-04-04 17:08:27.677 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-04 17:08:27.677 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2008-04-04 17:08:28.679 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-04 17:08:28.680 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2008-04-04 17:08:31.131 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-04 17:08:31.132 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2008-04-04 17:08:34.807 Deleting UPnP client...

```

Any suggestions to remedy this?

---

### Post by tamoneya on 2008-04-04
check to make sure that your mysql server can be access remotely.  Look at the /etc/mysql/my.cnf.

---

### Post by somuchfortheafter on 2008-04-04
here is the file, I am not really that proficient in sql so some help please.

```

$ cat /etc/mysql/my.cnf 
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
log_bin			= /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#
!includedir /etc/mysql/conf.d/

```

---

### Post by tamoneya on 2008-04-04
```
bind-address		= 127.0.0.1

``` is your problem.  This says that the mysql server can only be accessed from local host.  Comment this line out and restart your mysql server with ```
sudo /etc/init.d/mysqld restart
```

---

### Post by somuchfortheafter on 2008-04-05
ok I made the changes to the config file and restarted the server. Problem still exists. Could this be because the laptop is using eeexubuntu instead of generic ubuntu or even xubuntu?
Here is the file now:
```

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           = 127.0.0.1
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
thread_cache_size       = 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log            = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
log_bin                 = /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#
!includedir /etc/mysql/conf.d/

```

---

