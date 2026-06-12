---
title: "installing libboost for fb303"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by zeeple on 2009-01-16
Hi folks, I am working on a scribe/thrift setup and the problem I am running into is that when I do a ./bootstrap.sh in the fb303 directory I get the following error:

checking for boostlib >= 1.33.1... configure: error: We could not detect the boost libraries (version 1.33 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See [http://randspringer.de/boost](http://randspringer.de/boost) for more documentation.

My boost root is /usr/local/boost, and it only has two dirs in it, include, and lib.  the lib dir is completely empty.  So i figure I need to install libboost:

apt-get install libboost*

Which yield the errors similar to:

The following packages have unmet dependencies:
  libboost-date-time1.35-dev: Conflicts: libboost-date-time-dev but 1.34.1-11ubuntu1 is to be installed
  libboost-filesystem1.35-dev: Conflicts: libboost-filesystem-dev but 1.34.1-11ubuntu1 is to be installed

How does one resolve this?  Any suggestions would be helpful.

---

### Post by tasuki on 2009-08-30
Your post actually helped me a lot - I didn't know the packages were called 'libboost'.

To answer the question for anyone else googling this, simply install 'libboost-dev' (which installs all 1.34 packages and leaves 1.35 alone, at least in Intrepid).

---

