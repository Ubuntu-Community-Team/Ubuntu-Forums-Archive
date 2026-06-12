---
title: "compile from source"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by wirate on 2009-08-05
some software provide source files and not a deb package. How do I get the software running from source?

---

### Post by wizard10000 on 2009-08-05
> **waqar said:**
> some software provide source files and not a deb package. How do I get the software running from source?

First you read the install readme, generally named INSTALL.  That file should tell you what dependencies the program has and how to configure and install it.

Once the dependencies are satisfied it generally goes like this -

./configure

make

sudo make install

---

### Post by Sef on 2009-08-05
Read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by MrWES on 2009-08-05
> **wizard10000 said:**
> First you read the install readme, generally named INSTALL.  That file should tell you what dependencies the program has and how to configure and install it.

Once the dependencies are satisfied it generally goes like this -

./configure

make

sudo make install

You might want to look into using checkinstall, for use with installing apps from the source:

[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by shae on 2009-08-05
You may also consider searching for the program on Launchpad PPAs:
[https://launchpad.net/](https://launchpad.net/)

---

### Post by wirate on 2009-08-06
> **Sef said:**
> Read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").
that helped :)

---

