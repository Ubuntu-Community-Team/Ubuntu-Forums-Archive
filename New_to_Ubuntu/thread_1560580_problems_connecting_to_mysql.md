---
title: "problems connecting to mysql"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by mkarthik90 on 2010-08-25
[I][SIZE=3]Hi,
The Lampp package has been installed at /opt and when the lampp is  started the mysql server is not started and the following error occurs.  please note the pastebin for details.

[http://pastebin.com/NC3E9mXR](http://pastebin.com/NC3E9mXR)[/SIZE][SIZE=3]

The error is also attached here for reference

[/SIZE][/I]kkn@ubuntu:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
kkn@ubuntu:~$ /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

[SIZE=3][I]When i try to open the [http://localhost](http://localhost) the xampp is not loaded ? What should be done to install the mysql server successfully in the/opt/lampp directory? 

Regards,
Karthikeyan.M
[/I][/SIZE]

---

### Post by theDaveTheRave on 2010-08-25
Hi,

first question is are you able to start MySQL separately from the CLI?


From a terminal use the following. 

otherwise start and stop the server in 'non-safe' mode.
```

sudo /etc/init.d/mysql.server stop
sudo /etc/init.d/mysql.server start

```

I suggest trying the 'stop' version first, if you are already using Mysql in safe mode it will automatically try to re-start itself.

If you have the server starting at startup you want to use the 'safe' mode,this will attempt to restart the server if it dies for any reason.

```

bin/mysqld_safe --user=mysql &

```

if you are still uncertain the following 
```

ps aux|grep mysql

```
will show all currently running mysql for all users, you should get 3 lines, first is for the 'root' who is running the mysql daemon, second is the 'mysql' superuser that the server runs as, and third is your username running the ps aux|grep mysql command.


If not are you sure you have correctly installed the grant tables?
This is the link to the official [documentation]("http://dev.mysql.com/doc/refman/5.1/en/post-installation.html"), note this is the reference manual for version 5.1 ~ you version may be different so you will need to check with the following..

```

mysql --version

```

will confirm this, put the details of this in your next post.

Read the rest of the page that I linked to it has a lot of further information, like confirming the data directory for your install and alternative methods of starting up your server as system startup.

if you still can't get the server going drop a note back to the forum.

If you do get it going however, there is info in the link to connect to your server.

good luck, and remember to put a note on the thread if the above has helped (and what you did).

David

---

