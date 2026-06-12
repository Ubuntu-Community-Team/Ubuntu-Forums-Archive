---
title: "wxpython on Ubuntu 9.10 Karmic?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by e.sitarski on 2009-11-11
Apologies in advance if I am missing something obvious here.

I just clean-installed Ubuntu 9.10 Karmic.
The documentation suggests that wxpython is included, however, "import wx" in python fails with ImportError.

The wxgtk package is not listed in the Package Manager.

Trying to install it from [http://packages.ubuntu.com/karmic/python/python-wxgtk2.8](http://packages.ubuntu.com/karmic/python/python-wxgtk2.8) fails  (Error: Dependency is not satisfiable: python-wxversion (>= 2.8.9.1-0ubuntu6).

What am I missing?  Thanks.

---

### Post by drascus on 2009-11-11
go to terminal and type: sudo apt-get install python-wxgtk2.8

That along with it's dependencies that it will automatically installed should solve your problem.

---

### Post by e.sitarski on 2009-11-11
That worked.  Thank you.

---

