---
title: "/etc/init.d/mysql"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-06-01
I accidentally deleted /etc/init.d/mysql
Now I cannot install, remove, purge, autoremove etc. mysql-server-5.1
It is giving me problem installing: gdesklets
I could not uninstall mysql from synaptic either.
I have xampp, so I do not require this mysql.
Is there a way to recover /etc/init.d/mysql file, or remove it completely or anything to solve the problem?

---

### Post by seawolf167 on 2011-06-01
How did you solve the problem? If you post your solution, others happening on your thread with the same issue can see your solution and fix their issue as well.

---

### Post by RobikShrestha on 2011-06-01
I haven't solved the problem.

---

### Post by marios88 on 2011-06-01
you should try reinstalling it, but make sure you have a backup first using "mysqldump" or phpmyadmin

sudo apt-get install -f mysql

---

### Post by seawolf167 on 2011-06-01
> **RobikShrestha said:**
> I haven't solved the problem.

You should remove the "SOLVED" tag from the thread then so people won't skip over the thread.

---

### Post by RobikShrestha on 2011-06-01
It does not work.
I do not know how to make it "UNSOLVED".


robik@dhcppc0:~$ sudo apt-get install -f mysql
[sudo] password for robik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql
robik@dhcppc0:~$ sudo apt-get install -f mysql-server-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
mysql stop/waiting
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by james killbery on 2011-06-17
I've just installed mysql 5.1
my version of the file you have deleted is just a pointer to /lib/init/upstart-job.
so if you are lucky  you can recreate the pointer and save yourself re-installing

---

