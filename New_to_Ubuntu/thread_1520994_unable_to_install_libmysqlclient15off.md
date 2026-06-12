---
title: "unable to install libmysqlclient15off"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by dharmesh9 on 2010-06-30
I have libmysqlclient16 running on my computer

I wnat to install a server(APE) using .deb package but m getting errors  : 
  Package libmysqlclient15off is not installed.

So, I tried installing libmysqlclient15off using apt-get, but this package is not available for ubuntu 10.04

So, I downloaded it from karmic,but stil m gettin error

dpkg: error processing libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb (--install):

Plz help me out,m new to linux !!!!!

Thnx in advance.

Dharmesh9

---

### Post by tueor on 2010-07-04
Hey 

Had the same issues running
sudo dpkg -i libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb

Mine was resolved by installing the mysql-common which is a dependency for the package.

cheers

---

