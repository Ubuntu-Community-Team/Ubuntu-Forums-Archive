---
title: "Help with PHPmyAdmin"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by D_2 on 2010-08-01
I am trying to get PHPmyadmin to connect to mySQL. I have uninstalled  phpmyadmin and reinstalled it again also went through all of the setup  questions. I can get to it with my browser and put in a username and  password but when I click on the go button all that happens is the  screen refreshes and it doesn't let me in. I have Webmin and looked  under the mysql area and phpmyadmin does have a database in there, I do  see different usernames and passwords, I have root, phpmyadmin as just 2  of the users. What can I do to get this to log into mysql so I can use  it to use mySQL.
 
Thanks for your help
D2

---

### Post by cariboo on 2010-08-01
Make sure you have mysql-server-5.1 installed and running.

Ssh into your server and at the prompt type:

```
ps ax | grep mysql
```

the result of the above command should look similar to this:

```
ps ax | grep mysql
 3149 pts/0    S+     0:00 grep --color=auto mysql
 5443 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 5551 ?        Sl     5:59 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
 5552 ?        S      0:00 logger -t mysqld -p daemon.error
```

If you don't get an output similar to the above try starting mysql, at the same prompt, if you are running a server version before Kamic type:

```
sudo /etc/init.d/mysql-server-X
```

where X is the mysql server version. For Karmic and newer type:

```
sudo service mysql-server-X start
```

again X = version number. In the example above, I'm running mysql-server-5.1

---

### Post by D_2 on 2010-08-01
Thank you for your reply cariboo907. Here is my output when i run the command

ps ax | grrep mysql

2507 ?          Ssl  1:25  /usr/sbin/mysqld
11509 pts/0  S+   0:00 grep --color=audo mysql

I am running mysql 5.1.41 from what Webmin says it is. I did try to run 

sudo /etc/init.d/mysql-server-5.1

and got back command not found

I even tried it again using mysql-server-5.1.41 and got back the same thing of command not found.

What does this say that is going on if anything. What is the next step. I can stop and restart mysql in webmin and that doesn't seem to help any.

---

