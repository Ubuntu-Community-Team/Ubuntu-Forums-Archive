---
title: "Can't install python boost library"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by irate.turtle on 2009-11-26
What am I doing wrong?

```
$ apt-cache search libboost-python
libboost-python1.38-dev - Boost.Python Library development files
libboost-python1.38.0 - Boost.Python Library
libboost-python-dev - Boost.Python Library development files (default version)
libboost-python1.34.1 - Boost.Python Library
libboost-python1.40-dev - Boost.Python Library development files
libboost-python1.40.0 - Boost.Python Library
$ [COLOR="Red"]sudo apt-get  install libboost-python-dev[/COLOR]
...
$ [COLOR="Red"]python[/COLOR]
Python 2.6.4 (r264:75706, Nov  2 2009, 14:44:17) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> [COLOR="Red"]import boost
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named boost[/COLOR]
>>> 
$ uname -a
Linux xxxxx 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
$ cat /etc/issue
Ubuntu 9.10 \n \l

```

---

### Post by yeats on 2009-11-26
Why don't you try installing one of the non -dev versions?  I'm not familiar with the module, so I can't advise as to which version would do what (1.38 ~ 1.40)...

---

### Post by ilil on 2009-11-26
Well, Boost is not Python-based, it is C++-based! And libboost-python is binding to call Python from C++. I am not sure Python can call C++ with Boost.

---

### Post by irate.turtle on 2009-11-26
> **chrissharp123 said:**
> Why don't you try installing one of the non -dev versions?  I'm not familiar with the module, so I can't advise as to which version would do what (1.38 ~ 1.40)...

I tried all one by one. Doesn't work

> **ilil said:**
> Well, Boost is not Python-based, it is C++-based! And libboost-python is binding to call Python from C++. I am not sure Python can call C++ with Boost.

You can call boost from python. Or so says this [ppt]("http://vw.indiana.edu/talks-spring06/doug.ppt")

Maybe I am using the wrong package, or maybe the package doesn't exist in repository.

---

### Post by irate.turtle on 2009-11-27
> **irate.turtle said:**
> ... maybe the package doesn't exist in repository.

Probably its true ... [URL="http://www.osl.iu.edu/~dgregor/bgl-python/"]Boost Graph Library - Python Bindings
[/URL]

---

