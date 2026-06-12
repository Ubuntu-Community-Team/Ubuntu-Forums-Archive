---
title: "Find out if package exists in a version of Ubuntu?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Swerve1000 on 2009-11-05
Hi,

I was wondering how I could find out which version of a package exists in a version of Ubuntu.

Specifically I need to find out if a package called libtool is version 1.5.x.x in Ubuntu version 8.04LTS.

I have a copy of that version, but was hoping I wouldn't have to install it just to find this out.

Thanks for any advice, it most appreciated!

---

### Post by philinux on 2009-11-05
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Have a browse.

---

### Post by ashishmalik10 on 2009-11-05
Type following in the command line :
> $apt-cache showpkg libtool
This will list the package, if it is installed and show its version also.
It also show the dependencies for the libtool package.

or you cant try this to search for libtool package in your ubuntu
> $apt-cache search libtool

Have a nice day.   ):P

---

### Post by Swerve1000 on 2009-11-05
Thanks (chaps?) !

It is there :)

---

