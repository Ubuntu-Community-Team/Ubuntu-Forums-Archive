---
title: "update manager problem"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by suxxor on 2008-06-07
this is error which shows me update manager when i try to start it 

  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 


this is error which shows me update manager when i try to start it 


this is output of " dpkg --configure -a "

   1.
      dpkg --configure -a
   2.
      Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
   3.
       * Stopping MySQL database server mysqld                                 [ OK ]
   4.
      Reloading AppArmor profiles /sbin/apparmor_parser: Unable to replace "/usr/lib/cups/backend/cups-pdf".  Profile doesn't conform to protocol
   5.
       Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
   6.
      Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
   7.
      /sbin/apparmor_parser: Unable to replace "/usr/sbin/mysqld".  Profile doesn't conform to protocol
   8.
       Profile /etc/apparmor.d/usr.sbin.mysqld failed to load
   9.
      : Failed.
  10.
      invoke-rc.d: initscript apparmor, action "force-reload" failed.
  11.
       * Starting MySQL database server mysqld                                 [ OK ]
  12.
      /etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
  13.
      invoke-rc.d: initscript mysql, action "start" failed.


somebody to help =S

---

### Post by forger on 2008-06-07
which ubuntu release is this? ubuntu hardy heron 8.04?
try:
```

sudo apt-get -f install
sudo apt-get purge mysql-server-5.0 mysql-server
sudo apt-get install --reinstall apparmor cups-pdf
sudo apt-get install mysql-server

```

** If it doesn't work **
try this:
i386 / x86 (32-bit ubuntu):
```

cd $HOME
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.1+1075-0ubuntu9.1_i386.deb
sudo dpkg -i apparmor_2.1+1075-0ubuntu9.1_i386.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/c/cups-pdf/cups-pdf_2.4.6-4ubuntu2_i386.deb
sudo dpkg -i cups-pdf_2.4.6-4ubuntu2_i386.deb

```

amd64 / x86_64 (64-bit ubuntu):
```

cd $HOME
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.1+1075-0ubuntu9.1_amd64.deb
sudo dpkg -i apparmor_2.1+1075-0ubuntu9.1_amd64.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/c/cups-pdf/cups-pdf_2.4.6-4ubuntu2_amd64.deb
sudo dpkg -i cups-pdf_2.4.6-4ubuntu2_amd64.deb

```

after the above, do:
```

sudo apt-get -f install
sudo apt-get purge mysql-server-5.0 mysql-server
sudo apt-get install --reinstall apparmor cups-pdf
sudo apt-get install mysql-server

```

---

### Post by suxxor on 2008-06-07
doesn`t work after second way i the same output with dpkg --configure -a

---

### Post by forger on 2008-06-08
hmmm looks like apparmor is giving you hard time, have you tampered with /etc/mysql/my.cnf [myslqd] section?

you could try stopping apparmor before doing the dpkg command:
```
sudo /etc/init.d/apparmor stop
```
then restart it
```
sudo /etc/init.d/apparmor start
```

*or* you can disable the mysql / cupsys warnings using:
```

sudo rm /etc/apparmor.d/usr.sbin.cupsd
sudo apt-get install --reinstall cupsys
sudo rm /etc/apparmor.d/force-complain/usr.sbin.mysqld
sudo ln -s /etc/apparmor.d/usr.sbin.mysql /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.sbin.mysql
```

---

### Post by suxxor on 2008-06-08
yes i didn`t mentioned , when i was running on ubuntu 7.10 , typing "whereis mysql" and then deleted all directories containing mysql , i did this because i was using lampp and i didn`t want to stop the default mysql server every time i do the same thing for apache server , but this was very stupid :( , and after upgrade on 8.04  this happened 

kaloqn@kaloqn-desktop:~$ sudo /etc/init.d/apparmor stop
[sudo] password for kaloqn: 
Unloading AppArmor profiles : done.
kaloqn@kaloqn-desktop:~$ sudo /etc/init.d/apparmor start
Loading AppArmor profiles /sbin/apparmor_parser: Unable to add "/usr/lib/cups/backend/cups-pdf".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
/sbin/apparmor_parser: Unable to add "/usr/sbin/mysqld".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.mysqld failed to load
: Failed.

kaloqn@kaloqn-desktop:~$ sudo rm /etc/apparmor.d/usr.sbin.cupsd

kaloqn@kaloqn-desktop:~$ sudo apt-get install --reinstall cupsys
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
kaloqn@kaloqn-desktop:~$ sudo rm /etc/apparmor.d/force-complain/usr.sbin.mysqld

kaloqn@kaloqn-desktop:~$ sudo ln -s /etc/apparmor.d/usr.sbin.mysql /etc/apparmor.d/disable/

kaloqn@kaloqn-desktop:~$ sudo apparmor_parser -R /etc/apparmor.d/usr.sbin.mysql
Error: Could not read profile /etc/apparmor.d/usr.sbin.mysql: No such file or directory.

kaloqn@kaloqn-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

kaloqn@kaloqn-desktop:~$ sudo su
root@kaloqn-desktop:/home/kaloqn#  dpkg --configure -a
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles /sbin/apparmor_parser: Unable to replace "/usr/sbin/mysqld".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.mysqld failed to load
: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

---

### Post by Bubba64 on 2008-06-08
You have to run sudo dpkg --configure -a  for it to work.

---

### Post by forger on 2008-06-08
suxxor let's try once more
we're entering the **dangerous** zone, you use these commands at **your own risk**
```

sudo dpkg -P mysql-server-5.0
sudo dpkg -P mysql-server
sudo dpkg -P apparmor
sudo rm -rf /etc/apparmor.d/
sudo dpkg --configure -a
sudo apt-get install --reinstall mysql-server apparmor

```

---

### Post by suxxor on 2008-06-08
workz thanx a lot for the help

---

