---
title: "Can't connect to local MySQL server through socket"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Amw088 on 2009-01-29
I installed xampp and everything was working fine untill I wanted to login into mysql to make usernames pws and dbs. but when ever I try to connect via terminal I get 

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


when I think it should be looking in 
/opt/lampp/blah/blah

Any idea how I would change this?

---

### Post by Cypher on 2009-01-29
It's looking in the right place, try 
```

sudo /etc/init.d/mysqld restart

```
and see if the file /var/run/mysqld/mysqld.sock was created, if not, do
```

sudo touch /var/run/mysqld/mysqld.sock

```
and then restart the daemon with the first command and see if things behave better..

---

### Post by Amw088 on 2009-01-29
For the first one I got 

sudo: /etc/init.d/mysqld: command not found

then on the second one i get 

touch: cannot touch `/var/run/mysqld/mysqld.sock': No such file or directory

---

### Post by Cypher on 2009-01-29
OK..the init script is actually /etc/init.d/mysql and I usually don't install Apache, PHP and MySQL using the XAMPP method on Linux as it's easy to install them individually and with Ubuntu they auto-configure and get going quickly.

On Windows XAMPP is a lifesaver.

Having said that, can you search to see if XAMPP installed an individual mysql package with
```

dpkg -l | grep mysql

```
Also try the following
```

sudo mkdir /var/run/mysqld
sudo /etc/init.d/mysql restart

```
If you get an error with the second command here, you might want to actually check to see if that file exists in the /etc/init.d directory..

---

### Post by Amw088 on 2009-01-29
first one ran fine, second one I got this

* Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail]

When I go to start mysql with /opt/lampp/lampp startmysql it says it's already runing and when I try to login to mysql I still get the origanil error.

---

### Post by Amw088 on 2009-01-29
Well I unistalled Xampp - restarted - installed xampp - restarted - then went to start it - try and get into mysql - then stoped it.

anthony@anthony-desktop:~$ sudo /opt/lampp/lampp start
[sudo] password for anthony: 
Starting XAMPP for Linux 1.7...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
anthony@anthony-desktop:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
anthony@anthony-desktop:~$ sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.7...
XAMPP: XAMPP-Apache is not running.
XAMPP: XAMPP-MySQL is not running.
XAMPP: Stopping ProFTPD...
XAMPP stopped.
anthony@anthony-desktop:~$

---

### Post by unutbu on 2009-01-29
Perhaps, if you are willing to uninstall Xampp, give the Ubuntu official packages a try:
```
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install proftpd
sudo apt-get install mysql-server mysql-client

```

I'm not familiar with Xampp, so I'm not sure if this reproduces everything that Xampp does. However, I think there is a very good chance all the functionality you are looking for is in some package available in the official repositories, (and we should be able to help you find it if you tell us what is missing from the above packages).

---

### Post by Cypher on 2009-01-29
I agree with **unutbu**'s sentiments about using the native packages as opposed to XAMPP. As I stated above I've used the individual packages with great success and can better debug any issues there than with XAMPP..

---

### Post by Amw088 on 2009-01-29
Alright yea I'll give that one a try.

Thanks.

---

### Post by Amw088 on 2009-01-29
quick question. is there a easy way to delete all apache/mysql from sytem because when I try the link you gave mme I get a "newest version already installed" return

---

### Post by unutbu on 2009-01-29
Maybe try this:
```
sudo apt-get purge apache2
sudo apt-get purge php5
sudo apt-get purge proftpd
sudo apt-get purge mysql-server mysql-client
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install proftpd
sudo apt-get install mysql-server mysql-client

```

---

### Post by Amw088 on 2009-01-29
> **unutbu said:**
> Maybe try this:
```
sudo apt-get purge apache2
sudo apt-get purge php5
sudo apt-get purge proftpd
sudo apt-get purge mysql-server mysql-client
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install proftpd
sudo apt-get install mysql-server mysql-client

```

Ok, cool that worked..

Installed it all everything except proftpd which hung when trying to dl from some archive..

But still getting the 

anthony@anthony-desktop:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
anthony@anthony-desktop:~$ sudo /etc/init.d/mysqld restart
sudo: /etc/init.d/mysqld: command not found
anthony@anthony-desktop:~$ sudo touch /var/run/mysqld/mysqld.sock
touch: cannot touch `/var/run/mysqld/mysqld.sock': No such file or directory
anthony@anthony-desktop:~$ sudo mkdir /var/run/mysqld
anthony@anthony-desktop:~$ sudo /etc/init.d/mysql restart
sudo: /etc/init.d/mysql: command not found
anthony@anthony-desktop:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
anthony@anthony-desktop:~$

---

### Post by unutbu on 2009-01-29
Please post
```
apt-cache policy mysql-server-5.0
ls -l /etc/init.d | grep mysql
```

The first command should return something like
```

mysql-server-5.0:
  Installed: 5.0.67-0ubuntu6
  Candidate: 5.0.67-0ubuntu6
  Version table:
 *** 5.0.67-0ubuntu6 0
        500 http://gpl.savoirfairelinux.net intrepid/main Packages
        100 /var/lib/dpkg/status
```

The second command should return 
```

-rwxr-xr-x 1 root root  5755 2008-09-19 08:01 mysql
-rwxr-xr-x 1 root root  2515 2008-09-19 08:01 mysql-ndb
-rwxr-xr-x 1 root root  1905 2008-09-19 08:01 mysql-ndb-mgm
```
The fact that you get this error:
```

anthony@anthony-desktop:~$ sudo /etc/init.d/mysql restart
sudo: /etc/init.d/mysql: command not found
```
suggests that mysql-server-5.0 did not get installed correctly, since /etc/init.d/mysql is one of the files that it provides.

If your bandwidth can stand the beating, I'd suggest doing this
```

sudo apt-get install --reinstall mysql-server-5.0
```
and then carefully reading through the output for any errors. If you find any, post them and maybe we'll know what to do about them.

Edit: Actually, the mysql-server-5.0 package may still be on your system in /var/cache/apt/archives, so the "sudo apt-get install --reinstall" command above might not actually demand any network bandwidth. How about give it a try and tell us how it goes.

---

### Post by Amw088 on 2009-01-29
Last command seemed to work till end where i got this

invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
Reloading AppArmor profiles : done.

---

### Post by unutbu on 2009-01-29
What is the output of these commands?
```
apt-cache policy mysql-server-5.0
ls -l /etc/init.d
```

---

### Post by (Pato)² on 2009-01-30
XAMPP for linux is a stand-alone app. I prefer it to the native packages as I dislike its configuration.

To solve you problem yo can do this:
$sudo su
#gedit /etc/mysql/my.cnf

And on line number 21 replace "/var/run/mysqld/mysqld.sock" with "/opt/lampp/var/mysql/mysql.sock"

Save it, and it should work fine now :)

(I had the same problem just a minutes ago :p)

---

### Post by alextintea on 2009-04-18
# /etc/init.d/mysql start
Starting MySQL database server: mysqld.
...failed or took more than 6s.
Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

**Solution:**

The following command saves the corrupted file, it generates new and then start MySQL:

cp /var/log/mysql/mysql-bin.index /var/log/mysql/mysql-bin.index.back;
ls --format=single-column /var/log/mysql/mysql-bin.0* >/var/log/mysql/mysql-bin.index;
/etc/init.d/mysql restart;

---

### Post by mistaguy on 2010-09-30
-the problem could that mysql server is not started....you can work  around it using the following options:
 (1)use
 root@wazzabanga:/home/mistaguy# mysqld -u root
 the server should start and so u can now access mysql using
 root@wazzabanga:/home/mistaguy# mysql u root p
 (2)incase this fails; use the option
 root@wazzabanga:/home/mistaguy# mysqld --verbose --help
 this will give u options that u can use to start the server. u can use  the following but its risky in that any one can access your server
 root@wazzabanga:/home/mistaguy# mysqld --skip-grant-tables
 punch in the following to access the mysql
 root@wazzabanga:/home/mistaguy# mysql
 once mysql is okay by using any of the options above, u can access  phpmysqladmin from your browser as usual provided u provide the okay  user  details

---

### Post by aaricia on 2010-10-01
I have the same problem, so I am going to try some  of the tips they mention here.

I am not an advanced user, but I think that to delete old files you need un-install Apache:

sudo apt-get autoremove apache2

---

