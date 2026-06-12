---
title: "Installing python2.5 on Maverick"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by vivek40 on 2010-10-12
Hii I wanted to install python2.5.4 on my system and went about compling from source like this.
[COLOR=#000000][FONT=Times New Roman][FONT=arial]1.I downloaded Python-2.5.4.tgz.tar from the python site.
```

[COLOR=#000000][FONT=Times New Roman][FONT=arial]cd Downloads[COLOR=#333333][FONT=Georgia]tar -xvzf Python-2.5.4.tgz.tar cd Python-2.5.4
 ./configure --prefix=/usr/local/python2.5.4 
make 
make test 
sudo make install 
sudo ln -s /usr/local/python2.5.4/bin/python /usr/bin/python2.5.4 [/FONT][/COLOR]
[/FONT][/FONT][/COLOR]
```However after installing it, when I try using it , I get the below error:-
File "/home/vivek/google_appengine/google/appengine/datastore/datastore_sqlite_stub.py", line 52, in <module>
    import sqlite3
  File "/usr/local/python2.5.4/lib/python2.5/sqlite3/__init__.py", line 24, in <module>
    from dbapi2 import *
  File "/usr/local/python2.5.4/lib/python2.5/sqlite3/dbapi2.py", line 27, in <module>
    from _sqlite3 import *
ImportError: No module named _sqlite3



How do I get to solve this.Would Python not come bundled with sqlite3. Need someone to help me here please!

[/FONT][/FONT][/COLOR]

---

### Post by marcello.nuccio on 2010-11-08
You can use the packages in
[https://launchpad.net/~fkrull/+archive/deadsnakes]("https://launchpad.net/%7Efkrull/+archive/deadsnakes")
available for Lucid and Maverick releases.

---

### Post by godspeedmav on 2010-11-08
> **vivek40 said:**
> Hii I wanted to install python2.5.4 on my system and went about compling from source like this.
[COLOR=#000000][FONT=Times New Roman][FONT=arial]1.I downloaded Python-2.5.4.tgz.tar from the python site.
```

[COLOR=#000000][FONT=Times New Roman][FONT=arial]cd Downloads[COLOR=#333333][FONT=Georgia]tar -xvzf Python-2.5.4.tgz.tar cd Python-2.5.4
 ./configure --prefix=/usr/local/python2.5.4 
make 
make test 
sudo make install 
sudo ln -s /usr/local/python2.5.4/bin/python /usr/bin/python2.5.4 [/FONT][/COLOR]
[/FONT][/FONT][/COLOR]
```However after installing it, when I try using it , I get the below error:-
File "/home/vivek/google_appengine/google/appengine/datastore/datastore_sqlite_stub.py", line 52, in <module>
    import sqlite3
  File "/usr/local/python2.5.4/lib/python2.5/sqlite3/__init__.py", line 24, in <module>
    from dbapi2 import *
  File "/usr/local/python2.5.4/lib/python2.5/sqlite3/dbapi2.py", line 27, in <module>
    from _sqlite3 import *
ImportError: No module named _sqlite3



How do I get to solve this.Would Python not come bundled with sqlite3. Need someone to help me here please!

[/FONT][/FONT][/COLOR]

According to this post: _[http://stackoverflow.com/questions/1210664/no-module-named-sqlite3](http://stackoverflow.com/questions/1210664/no-module-named-sqlite3)_ on stackoverflow.com, it is very similar to your problem. it says here that the user installed libsqlite3-dev from synaptic package manager, and recompiled python2.5 or as in your case python2.5.4. If you want to compile yourself, try this one or use the tip above. :)

---

