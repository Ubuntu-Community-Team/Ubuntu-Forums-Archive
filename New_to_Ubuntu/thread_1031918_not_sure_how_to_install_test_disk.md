---
title: "not sure how to install test disk"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by nynoah on 2009-01-05
I want to install the latest version of Testdisk utilities.  The version in the Repos is only 6.08 and there is a 6.1 that I want to use to recover some lost stuff.  I downloaded it but I can not figure out how to get it installed.  Any one know what I need to do?

I got it from here
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by logos34 on 2009-01-05
just dl, unzip and run the static binary straight frorm the folder--don't even need to install it:
> 
Linux, kernel 2.6.x i386/x86_64, tar.bz2

tar xjvf testdisk-6.10.linux26.tar.bz2

cd testdisk-6.10/linux

sudo ./testdisk_static

---

### Post by nynoah on 2009-01-05
Thanks I will try that then.

---

### Post by logos34 on 2009-01-05
And if you decide you want to install it:

dl the [Source, tar.bz2.]("http://www.cgsecurity.org/testdisk-6.10.tar.bz2"):

tar xjvf testdisk-6.10.tar.bz2

cd testdisk-6.10

./configure

make

sudo make install

make sure you have **build-essential** pkg installed

good luck and enjoy

---

