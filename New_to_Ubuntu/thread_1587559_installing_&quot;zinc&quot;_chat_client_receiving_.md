---
title: "installing &quot;zinc&quot; chat client receiving install error (newbie here)"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-10-03
Hi, all. I am new to linux and new to computing in general. I am  enjoying using more command-line, curses based programs. (Keep in mind  however that I am very new to all of this)

Situation: I am trying to install the Zinc yahoo chat client. Note: I am running a fully up-to-date Ubunbu 10.04 32bit. 

doing the following: ```
su -
wget http://larvalstage.com/zinc/files/zinc-1.1.11.tar.gz
tar xzf zinc-1.1.11.tar.gz
cd zinc-1.1.11 
mkdir /usr/lib/zinc
cp src/* /usr/lib/zinc/
ln -s /usr/lib/zinc/zinc /usr/bin/zinc
/usr/bin/zinc --install
cd ..
rm -rf zinc-1.1.11/
exit
```i then get the following error: 
```
$ zinc
/usr/lib/zinc/CommandHandler.py:23: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  import popen2
/usr/lib/zinc/YahooYMSG.py:22: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Traceback (most recent call last):
  File "/usr/bin/zinc", line 42, in <module>
    zinc.start()
  File "/usr/lib/zinc/Zinc.py", line 139, in start
    self.sess.load()
  File "/usr/lib/zinc/Session.py", line 260, in load
    self.login.load()        # load login
  File "/usr/lib/zinc/Login.py", line 336, in load
    roomnum = proflist[7].strip()
IndexError: list index out of range
```any help would be greatly appreciated

note: ```
$ python --version
Python 2.6.5

```.  if that has anything to do with it.

---

