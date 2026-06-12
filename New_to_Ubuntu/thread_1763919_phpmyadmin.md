---
title: "phpmyadmin"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-05-21
I removed mysql-server etc. by
sudo apt-get remove mysql-server
(Then i did a silly mistake:
by removing /etc/init.d/apache2 and /etc/init.d/mysql)


I installed xampp using tar file.

[http://localhost/xampp](http://localhost/xampp) works fine but
[http://localhost/phpmyadmin](http://localhost/phpmyadmin) shows following error message

#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

Following is the my.cnf file:

```

# Example MySQL config file for medium systems.
#
# This is for a system with little memory (32M - 64M) where MySQL plays
# an important part, or systems up to 128M where MySQL is used together with
# other programs (such as a web server)
#
# You can copy this file to
# /etc/my.cnf to set global options,
# mysql-data-dir/my.cnf to set server-specific options (in this
# installation this directory is /opt/lampp/var/mysql) or
# ~/.my.cnf to set user-specific options.
#
# In this file, you can use all long options that a program supports.
# If you want to know which options a program supports, run the program
# with the "--help" option.

# The following options will be passed to all MySQL clients
[client]
#password    = your_password
port        = 3306
socket        = /opt/lampp/var/mysql/mysql.sock

# Here follows entries for some specific programs

# The MySQL server
[mysqld]
user        = nobody
port        = 3306
socket        = /opt/lampp/var/mysql/mysql.sock
skip-external-locking
key_buffer = 16M
max_allowed_packet = 1M
table_cache = 64
sort_buffer_size = 512K
net_buffer_length = 8K
read_buffer_size = 256K
read_rnd_buffer_size = 512K
myisam_sort_buffer_size = 8M

# Where do all the plugins live
plugin_dir = /opt/lampp/lib/mysql/plugin/

# Don't listen on a TCP/IP port at all. This can be a security enhancement,
# if all processes that need to connect to mysqld run on the same host.
# All interaction with mysqld must be made via Unix sockets or named pipes.
# Note that using this option without enabling named pipes on Windows
# (via the "enable-named-pipe" option) will render mysqld useless!
# 
#skip-networking

# Replication Master Server (default)
# binary logging is required for replication
# log-bin deactivated by default since XAMPP 1.4.11
#log-bin=mysql-bin

# required unique id between 1 and 2^32 - 1
# defaults to 1 if master-host is not set
# but will not function as a master if omitted
server-id    = 1

# Replication Slave (comment out master section to use this)
#
# To configure this host as a replication slave, you can choose between
# two methods :
#
# 1) Use the CHANGE MASTER TO command (fully described in our manual) -
#    the syntax is:
#
#    CHANGE MASTER TO MASTER_HOST=<host>, MASTER_PORT=<port>,
#    MASTER_USER=<user>, MASTER_PASSWORD=<password> ;
#
#    where you replace <host>, <user>, <password> by quoted strings and
#    <port> by the master's port number (3306 by default).
#
#    Example:
#
#    CHANGE MASTER TO MASTER_HOST='125.564.12.1', MASTER_PORT=3306,
#    MASTER_USER='joe', MASTER_PASSWORD='secret';
#
# OR
#
# 2) Set the variables below. However, in case you choose this method, then
#    start replication for the first time (even unsuccessfully, for example
#    if you mistyped the password in master-password and the slave fails to
#    connect), the slave will create a master.info file, and any later
#    change in this file to the variables' values below will be ignored and
#    overridden by the content of the master.info file, unless you shutdown
#    the slave server, delete master.info and restart the slaver server.
#    For that reason, you may want to leave the lines below untouched
#    (commented) and instead use CHANGE MASTER TO (see above)
#
# required unique id between 2 and 2^32 - 1
# (and different from the master)
# defaults to 2 if master-host is set
# but will not function as a slave if omitted
#server-id       = 2
#
# The replication master for this slave - required
#master-host     =   <hostname>
#
# The username the slave will use for authentication when connecting
# to the master - required
#master-user     =   <username>
#
# The password the slave will authenticate with when connecting to
# the master - required
#master-password =   <password>
#
# The port the master is listening on.
# optional - defaults to 3306
#master-port     =  <port>
#
# binary logging - not required for slaves, but recommended
#log-bin=mysql-bin


# Point the following paths to different dedicated disks
#tmpdir        = /tmp/        
#log-update     = /path-to-dedicated-directory/hostname

# Uncomment the following if you are using BDB tables
#bdb_cache_size = 4M
#bdb_max_lock = 10000

# Comment the following if you are using InnoDB tables
#skip-innodb
innodb_data_home_dir = /opt/lampp/var/mysql/
innodb_data_file_path = ibdata1:10M:autoextend
innodb_log_group_home_dir = /opt/lampp/var/mysql/
# You can set .._buffer_pool_size up to 50 - 80 %
# of RAM but beware of setting memory usage too high
innodb_buffer_pool_size = 16M
innodb_additional_mem_pool_size = 2M
# Set .._log_file_size to 25 % of buffer pool size
innodb_log_file_size = 5M
innodb_log_buffer_size = 8M
innodb_flush_log_at_trx_commit = 1
innodb_lock_wait_timeout = 50

[mysqldump]
quick
max_allowed_packet = 16M

[mysql]
no-auto-rehash
# Remove the next comment character if you are not familiar with SQL
#safe-updates

[isamchk]
key_buffer = 20M
sort_buffer_size = 20M
read_buffer = 2M
write_buffer = 2M

[myisamchk]
key_buffer = 20M
sort_buffer_size = 20M
read_buffer = 2M
write_buffer = 2M

[mysqlhotcopy]
interactive-timeout
```

---

### Post by compmodder26 on 2011-05-21
Is mysql actually running?

---

### Post by RobikShrestha on 2011-05-21
robik@dhcppc0:~$ sudo /opt/lampp/lampp start

[sudo] password for robik: 
Starting XAMPP for Linux 1.7.4...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

It is already running but how many mysql's are there? How would I remove all the rest and keep just the one from xampp??

---

### Post by compmodder26 on 2011-05-21
Type this into a terminal.  If if gives you a number then that is the process ID of mysql.  If not, then you know mysql is not running

```
pgrep mysql
```

---

### Post by RobikShrestha on 2011-05-21
979, so the mysql is running. I would like to know how to stop it so that I can run mysql of lampp folder. Then, how to solve the problem of phpmyadmin? I removed mysql and apache2 from /etc/init.d. Is there a way to recover them?

---

### Post by compmodder26 on 2011-05-21
> **RobikShrestha said:**
> 979, so the mysql is running. I would like to know how to stop it so that I can run mysql of lampp folder. Then, how to solve the problem of phpmyadmin? I removed mysql and apache2 from /etc/init.d. Is there a way to recover them?

Without the init script, you can simply kill the mysql instance.  You now know that the process ID of mysql is 979.  So you can type "sudo kill -9 979".  That should kill the running mysql server.  Then try to restart lampp.

Do that and try to access phpmyadmin, then let us know what happens.

---

### Post by RobikShrestha on 2011-05-21
After I killed the process, and did: sudo /opt/lampp/lampp start
It still said that another mysql was running
I again killed mysql and then did pgrep mysql
It showed another pId
I killed that pId and did pgrep mysql again. It again showed another pId. Why isn't it killing mysql? 
[http://localhost/phpmyadmin::](http://localhost/phpmyadmin::) is as follows:
     **Welcome to  phpMyAdmin **

  
                          **Error**

      **MySQL said: **[[IMG]http://localhost/phpmyadmin/themes/original/img/b_help.png[/IMG]]("http://dev.mysql.com/doc/refman/5.0/en/error-messages-server.html") 
  #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured) 

Connection for controluser as defined in your configuration failed.

---

### Post by RobikShrestha on 2011-05-21
OK
I stopped mysql by
sudo service mysql stop
and then started lampp using:
sudo /opt/lampp/lampp start

And everything works fine

---

### Post by Oliphant on 2013-03-16
This got me up and running perfectly.  Thank you.

---

