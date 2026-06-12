---
title: "Missing mysql.sock"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by atulmittal_mds on 2011-04-13
Hi All,

Can anyone help me Understanding what should i need to do to solve the following error :
"Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' "

i am begginer and i need to install mysql on ubuntu..
i have written the follwing command

-> sudo apt-get install mysql-server
-> sudo apt-get install mysql-client
and when i had written sudo mysql -u root
it shows the above written error..

Please give me some solutions how can i install and start mysql..
Hope i would get some wonderful suggestions..

Cheers
Atul

---

### Post by Idiotji on 2011-04-15
What i am thinking that your folder permissions are changed by you.Contact to your admin he may solve this prob b formatiing the system:lolflag:

---

### Post by falko on 2011-04-15
Try to restart MySQL:
```
sudo /etc/init.d/mysql restart
```

If that still doesn't work, check your syslog (in the /var/log/ directory) and run ```
sudo netstat -tap | grep mysql
``` to see if MySQL is running.

---

### Post by kamaji792 on 2011-04-15
Hi Atul,

Not sure if this is still a live problem.  It is certainly not an un-common problem.  Try searching for "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' ".

Just a couple of points did you make sure mysqld was running:
```
ps -e | grep mysqld
```
The output on my system was:
```
 6240 pts/0    00:00:00 mysqld_safe
 6279 pts/0    00:00:06 mysqld
```

If you need to start mysql:
```
sudo /etc/init.d/mysql start
```

Additionally you don't need to sudo the mysql command; just:
```
mysql -u root -p
```

If you are still having problems then post here again and I will try an keep an eye on the thread

atb K :guitar:

---

