---
title: "What is the location where you usually store lib extra info."
date: 2011-07-20
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-07-20
And how do you move stuff there.

---

### Post by oldos2er on 2011-07-20
Do you mean /lib ? Since it's outside of your home folder, you need to use admin privileges to have write access to it ```
sudo cp libfoo /lib
``` Or graphically ```
gksudo nautilus
```

It would help if you would explain exactly what you're trying to do.

---

### Post by TheManno1 on 2011-07-20
Finally:  Get the source package at  [http://code.google.com/p/los-cocos/downloads/list](http://code.google.com/p/los-cocos/downloads/list)   Cocos is a pure python package, so the usual ways will work.  Note that cocos documentation and examples are included in the source  package.    unpack the source package and:   from the unpacked directory move the directories doc/html, test, samples,  utest to the location when you usually store lib extra info.     and then run  setup.py install

Doesn't seem to be working.

---

### Post by oldos2er on 2011-07-20
In that case I would unpack it in your home folder, and run setup.py install from there.

---

### Post by TheManno1 on 2011-07-20
I have absolutely no idea whether I have installed it or not now how do I run it in eclipse.A video tutorial on how to install would be nice.I copied the folders it say to both lib and home folder. Then runned setup from where I extracted it.

---

### Post by oldos2er on 2011-07-20
For specialized software like that it's probably best to get help through its website. Sorry I can't help you out more than that.

---

