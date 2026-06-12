---
title: "libxml2dom instalation"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by pedlazcar on 2011-05-18
Hello...

I'm trying to install the lixml2dom package, for python. I'm using ubuntu 11.04.
I have no idea how to start using it. I've downloaded the pacage from here: [http://www.boddie.org.uk/python/libxml2dom.html ]("http://www.boddie.org.uk/python/libxml2dom.html"). The only thing the README.txt says is the following:

> Making Packages
---------------

To make Debian-based packages:

  1. Create new package directories under packages if necessary.
  2. Make a symbolic link in the distribution's root directory to keep the
     Debian tools happy; choose one of the following:

     ln -s packages/ubuntu-hoary/python2.4-libxml2dom/debian/
     ln -s packages/ubuntu-feisty/python-libxml2dom/debian/
     ln -s packages/ubuntu-gutsy/python-libxml2dom/debian/
     ln -s packages/debian-sarge/python2.3-libxml2dom/debian/
     ln -s packages/debian-etch/python-libxml2dom/debian/
     ln -s packages/debian-lenny/python-libxml2dom/debian/

  3. Run the package builder:

     dpkg-buildpackage -rfakeroot

  4. Locate and tidy up the packages in the parent directory of the
     distribution's root directory.Can anyone explain in more details what I should do?

Tnahks!

---

### Post by JDBurnZ on 2011-05-24
Bump, exact same issue. Unable to find it in apt-get or easy_install.

---

### Post by RayDeCampo on 2011-06-01
I had the same problem.  The trick is to run the setup.py script:

```

$ chmod a+x setup.py
$ sudo ./setup.py install

```

---

