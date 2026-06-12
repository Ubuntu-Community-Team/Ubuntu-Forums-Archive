---
title: "can't shutdown mysqld"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by occams_beard on 2010-02-13
When ever I reboot or shutdown, I always get the message.

> 
Mysql shutdown..... Fail!


It always just refuses to shutdown.

I can not even stop it manually with

```

sudo /etc/init.d/mysql stop

``` 

It just returns [fail]

Today, there was an apt update of mysql and that failed too, because mysqld would not shut down. I had to forcefully stop mysqld with sudo kill in order to install the update.


Any ideas why this would be or how I can fix it?  

Thanks.

---

### Post by Shpongle on 2010-02-13
try killall mysql , if that doesnt work use top to find the process id (pid) then type kill %(insert pid here)

Edit: sorry i  misread it

---

### Post by occams_beard on 2010-02-14
bump. 

Still can't figure out what's going wrong, and worry about the DB not getting shut down cleanly...

Where does mysql store it's log files.

---

### Post by jd65pl on 2010-02-14
Logs are in
```
/var/log/mysql/
```
```
cat /var/log/mysql/error.log
```

mysql should be an upstart job but I doubt stopping it this way will have any impact on what you are seeing
```
sudo service mysql stop
```

---

### Post by occams_beard on 2010-02-14
Well, solved this my self. Turns out a while back I had destroyed the debian-sys-maint user account when I imported a DB from a server that was running CentOS. 

On Debian systems, this user apparently shuts down the DB, and various other maintenance stuff.

The solution was to simply recreate the user with:

```

GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;

```

Where '<password>' is the value found in /etc/mysql/debian.cnf.

Everything is working peachy again.

Anyway, learned something new :)

---

### Post by RedScourge on 2010-03-22
You do NOT need to grant all permissions, this is a bad habit to get into from a security standpoint.

All you need to grant is this (as root or whoever):

GRANT SHUTDOWN ON *.* TO 'debian-sys-maint'@'localhost';
GRANT SELECT ON `mysql`.`user` TO 'debian-sys-maint'@'localhost';

Because it needs to shutdown/startup, and does a test select from the users table as a sanity check to ensure the root user exists. This select is usually done by /usr/share/mysql/debian-start.inc.sh which is loaded by /etc/mysql/debian-start

---

