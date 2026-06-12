---
title: "Is there an alternative to taskcoach for linux ?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-10
Here is the windows xp program :

[http://www.taskcoach.org/screenshots/0.71.2-Windows_XP-Tasks_categories_and_effort.png](http://www.taskcoach.org/screenshots/0.71.2-Windows_XP-Tasks_categories_and_effort.png)

Is there something like this for LINUX ?

---

### Post by tpjk on 2010-01-10
have you tried the linux version of taskcoach? it is available as a .deb file here:

[http://www.taskcoach.org/download_for_linux.html](http://www.taskcoach.org/download_for_linux.html)

---

### Post by frenchn00b on 2010-01-10
> **tpjk said:**
> have you tried the linux version of taskcoach? it is available as a .deb file here:

[http://www.taskcoach.org/download_for_linux.html](http://www.taskcoach.org/download_for_linux.html)

thank you !

here are the sources: [http://downloads.sourceforge.net/project/taskcoach/taskcoach/Release-0.77.0/TaskCoach-0.77.0.tar.gz?use_mirror=ignum](http://downloads.sourceforge.net/project/taskcoach/taskcoach/Release-0.77.0/TaskCoach-0.77.0.tar.gz?use_mirror=ignum)

---

### Post by frenchn00b on 2010-01-10
[B]OK this is the working version for all distributions , whatever you have wxpython version too low.

It shall pass:

wget "http://downloads.sourceforge.net/project/taskcoach/taskcoach/Release%200.71.0/TaskCoach-0.71.0.tar.gz?use_mirror=sunet"
so that you have : 

```
TaskCoach-0.71.0
tar xvf TaskCoach-0.71.0.tar.gz
cd TaskCoach-0.71.0
python  taskcoach.py
```

Enjoy the alpha !
I hope that one day it enters our repositories[/B]

---

