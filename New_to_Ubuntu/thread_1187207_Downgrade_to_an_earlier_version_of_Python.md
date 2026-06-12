---
title: "Downgrade to an earlier version of Python"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Dru89 on 2009-06-14
I'm currently learning to use Google's [AppEngine]("http://code.google.com/appengine") and there are some bugs I've read about when compiling code for the appengine with python's version 2.6, they recommend 2.5.  Python 2.6 came readily installed on my computer when I installed Ubuntu 9.04.  Although, I believe I also have Python 2.5 installed.  How can I "downgrade" to Python 2.5?

Thanks,

Drew

---

### Post by lovinglinux on 2009-06-14
I recommend staying with Python 2.6, because Python 2.5 do not play well with Jaunty. It can cause high CPU usage.

---

### Post by ChaiTan on 2009-06-14
You can install python2.5 from synaptic and then use python2.5 as the command for running python instead of just python

---

### Post by zdmytriv on 2009-06-23
So how to downgrade from Python 2.5 to Python 2.6? 
I have some package dependencies on 2.5.

Thank you,
Zinovii

---

### Post by blackxored on 2009-06-23
install python2.5 python2.5-minimal
are your dependencies from source or from packages?

---

### Post by zdmytriv on 2009-06-23
The following packages have unmet dependencies:
  python-xapian: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is to be installed
E: Broken packages

AND

$sudo wajig install python2.5 python2.5-minimal
...
python2.5 is already the newest version.
python2.5-minimal is already the newest version.

---

### Post by zdmytriv on 2009-06-26
Problem solved.

I had in my sources.list url to debian/xapian. I just removed it and apt-get update and python-xapian installed like a charm.

Thanks everybody

---

