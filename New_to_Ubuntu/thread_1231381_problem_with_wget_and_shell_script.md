---
title: "problem with wget and shell script"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by gonzoga on 2009-08-04
Hey Guys,

I'm having a problem with wget and my shell script. Basically I'm learning how to set up a LAMP server not using Apt-get or anything. Also i decided to create a script too. so heres my script:

apt-get build-dep mysql-server php5 apache2 -y
apt-get install build-essential automake libtool g++ ncurses-dev -y
groupadd mysql
useradd -r -g mysql mysql
cd /
cd /home/test/
wget [http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz/from/http://mysql.mirror.redwire.net/](http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz/from/http://mysql.mirror.redwire.net/)
tar -xvf mysql-5.1.37.tar.gz
cd mysql-5.1.37
./configure --prefix=/usr/local/mysql
make
make install
cd scripts
./mysql_install_db
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/var
chgrp -R mysql /usr/local/mysql
cp support-files/my-medium.cnf /etc/my.cnf
PATH=$PATH:/usr/local/mysql/bin
cd /usr/local/mysql/bin/
./mysqld_safe --user=mysql &
cd /
cd /home/test/

This is where the problem is:
wget [http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz/from/http://mysql.mirror.redwire.net/](http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz/from/http://mysql.mirror.redwire.net/)

when i run it outside of the script it does just fine but inside of it it fails. It gives me a 'HTTP request sent, awaiting response... 404 Not Found.'

anyways any help is much appricated
Thanks

---

### Post by credobyte on 2009-08-04
Works just fine for me - maybe a temporary server issue ?

```
dainis@ubuntu:~$ cat demo.sh
wget http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz/from/http://mysql.mirror.redwire.net/
dainis@ubuntu:~$ ./demo.sh
--2009-08-04 21:04:17--  http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz/from/http://mysql.mirror.redwire.net/
Resolving dev.mysql.com... 213.136.52.29
Connecting to dev.mysql.com|213.136.52.29|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://mysql.mirror.redwire.net/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz [following]
--2009-08-04 21:04:18--  http://mysql.mirror.redwire.net/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz
Resolving mysql.mirror.redwire.net... 64.186.240.114
Connecting to mysql.mirror.redwire.net|64.186.240.114|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://mysql.west.mirrors.airband.net/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz [following]
--2009-08-04 21:04:19--  http://mysql.west.mirrors.airband.net/Downloads/MySQL-5.1/mysql-5.1.37.tar.gz
Resolving mysql.west.mirrors.airband.net... 64.186.242.210
Connecting to mysql.west.mirrors.airband.net|64.186.242.210|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35796850 (34M) [application/x-gzip]
Saving to: `mysql-5.1.37.tar.gz'

 0% [                                       ] 161,871     79.8K/s              ^Z
[1]+  Stopped                 ./demo.sh

```

---

### Post by gonzoga on 2009-08-06
hmm you right just doing wget alone in  the script works.... didn't  think of testing it alone in a script.  woops lol... must be something else causing it to freak
thanks

---

