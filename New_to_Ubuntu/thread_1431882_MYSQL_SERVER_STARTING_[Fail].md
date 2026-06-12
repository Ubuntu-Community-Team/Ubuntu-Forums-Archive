---
title: "MYSQL SERVER STARTING [Fail]"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by khaled_jamel on 2010-03-17
Hi 
after setting up mysql to use innodb as default storage engine and adding new file to configure some performance issue it fail to strat.

this is the error log :

Mar 17 11:09:57 Server mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Mar 17 11:09:57 Server mysqld: 100317 11:09:57 [Note] Plugin 'FEDERATED' is disabled.
Mar 17 11:09:58 Server mysqld: InnoDB: Error: log file ./ib_logfile0 is of different size 0 5242880 bytes
Mar 17 11:09:58 Server mysqld: InnoDB: than specified in the .cnf file 0 2013265920 bytes!
Mar 17 11:09:58 Server mysqld: 100317 11:09:58 [ERROR] Plugin 'InnoDB' init function returned error.
Mar 17 11:09:58 Server mysqld: 100317 11:09:58 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
Mar 17 11:09:58 Server mysqld: 100317 11:09:58 [ERROR] Unknown/unsupported table type: INNODB
Mar 17 11:09:58 Server mysqld: 100317 11:09:58 [ERROR] Aborting
Mar 17 11:09:58 Server mysqld: 
Mar 17 11:09:58 Server mysqld: 100317 11:09:58 [Warning] Forcing shutdown of 1 plugins
Mar 17 11:09:58 Server mysqld: 100317 11:09:58 [Note] /usr/sbin/mysqld: Shutdown complete
Mar 17 11:09:58 Server mysqld: 
Mar 17 11:09:58 Server mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
Mar 17 11:10:11 Server /etc/init.d/mysql[3994]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Mar 17 11:10:11 Server /etc/init.d/mysql[3994]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Mar 17 11:10:11 Server /etc/init.d/mysql[3994]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Mar 17 11:10:11 Server /etc/init.d/mysql[3994]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Mar 17 11:10:11 Server /etc/init.d/mysql[3994]: 


and this is my extra file added to configure performance 


[mysql]
default-character-set=utf8

[mysqld]
default-character-set=utf8
bind-address=0.0.0.0
lower_case_table_names = 1
innodb_file_per_table
innodb_buffer_pool_size=8053063680
innodb_log_file_size=2013265920
innodb_flush_log_at_trx_commit=0


i have proliant server with 10 GO memory size

thankx for your help

---

### Post by khaled_jamel on 2010-03-17
Resolution

It works now after deleted both ib_logfile0 and ib_logfile1 in /var/lib/mysql :D

---

