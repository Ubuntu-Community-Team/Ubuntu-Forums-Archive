---
title: "Installing modules for python 2.6"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by AlexanderSupertramp on 2009-04-03
Hi guys.

I have installed python2.6 along with systems default python (2.5) in intrepid.

2.6 is the version I am using for my development purpose, I have kept 2.5 for system dependencies.

Then I wanted python-mysqldb, I installed it with:
sudo apt-get install python-mysqldb.

But my python2.6 installation does not know that mysql adapter has been installed!!

I guess this happening because 2.5 is system installed, and is default.

So how should I install modules for 2.6?

Please note that, python2.6 is working fine. I have setup Aptana-pydev-django successfully, and can access python2.6 console from inside of Aptana.


Otherwise, can I make 2.6 default without causing any problems? if yes, how?

Thanks a lot for your time.

---

### Post by kevmitch on 2009-04-03
```

$ python
Python 2.6.1+ (r261:67515, Mar 28 2009, 16:27:16) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import MySQLdb
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
>>> 

```
Did you get the casing right?

---

### Post by AlexanderSupertramp on 2009-04-03
Thanks for the reply kevmitch.

Well it is DJango who is calling MySQLdb, not me directly.

So it can't be that. 

Moreover, after trying import:
```

$ python2.6
Python 2.6+ (r26:66714, Oct 22 2008, 09:25:02) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import MySQLdb
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named MySQLdb
>>> 

```

But it works with default install:

```

$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import MySQLdb
>>> 

```

Looks like python2.6 does not "know" MySQLdb obtained with: sudo apt-get install python-mysqldb.

Plus, it looks like on your system, python2.6.1 is default. Are you using Jaunty?

Mine is Intrepid.  2.5 is default python version.

Or do you knwo some way to make 2.6 default, and will that cause no problem?

Thanks again.

---

### Post by snova on 2009-04-03
Python modules, when installed, are tied to the version of the interpreter they were compiled against. You can try to modify the PYTHONPATH environment variable to include the place where python-mysqldb places its modules, but they are probably not going to work.

For example, I tried importing PyQt4:

```

$ PYTHONPATH=/usr/lib/python2.5/site-packages python2.6
Python 2.6.1 (r261:67515, Mar 15 2009, 20:51:22)                        
[GCC 4.3.2] on linux2                                                   
Type "help", "copyright", "credits" or "license" for more information.  
>>> from PyQt4.QtGui import QApplication
Traceback (most recent call last):      
  File "<stdin>", line 1, in <module>   
ImportError: /usr/lib/python2.5/site-packages/sip.so: undefined symbol: PyUnicodeUCS4_AsWideChar
>>>

```

This is not something that can be fixed with C modules, but if it is pure Python, it may work.

(Unfortunately the MySQL package has a C module, so probably not.)

---

### Post by kevmitch on 2009-04-05
Yeah, I'm using Jaunty. You might want to consider either moving to it or cherrypicking python packages from it if you want to play with 2.6. You can edit /usr/share/python/debian_defaults to change the default version.

---

### Post by AlexanderSupertramp on 2009-04-24
Sorry Guys. I solved the problem, but forgot to update the thread.

I finally compiled MySQLdb from source for python2.6.

Kept python2.5 as default.

It is working absolutely fine.


It was a twisted road but now I have Aptana + python2.6 + pyDev + DJango + MySQLdb + mysql5 on Ubuntu and I'm loving it. I can access python console from Aptana. :)


Thanks you for your time.

---

