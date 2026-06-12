---
title: "Pychess problems"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by coolkid5 on 2009-04-25
I just installed 9.04 Jaunty Jackalope and then PyChess from "Add/Remove programs."  However, when I click on PyChess from the applications menu nothing happens.  So I tried running 'pychess' from the terminal and got the following error message:

```
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/dist-packages/pychess/System/tsqlite.py", line 34, in run
    con = sqlite.connect(self.path)
OperationalError: unable to open database file

/usr/lib/python2.6/dist-packages/pychess/Players/engineNest.py:3: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import os, md5, imp

(pychess:9000): libglade-WARNING **: could not find glade file '/usr/lib/python2.6/glade/tipoftheday.glade'
Traceback (most recent call last):
  File "/usr/games/pychess", line 87, in <module>
    import pychess.Main
  File "/usr/lib/python2.6/dist-packages/pychess/Main.py", line 20, in <module>
    from pychess.widgets import tipOfTheDay
  File "/usr/lib/python2.6/dist-packages/pychess/widgets/tipOfTheDay.py", line 7, in <module>
    widgets = GladeWidgets("tipoftheday.glade")
  File "/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py", line 198, in __init__
    self.widgets = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
RuntimeError: could not create GladeXML object

```

---

### Post by conscious on 2009-04-26
This bug has already been reported:
[https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/356553](https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/356553)
[https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/365730](https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/365730)

---

### Post by coolkid5 on 2009-04-26
So does that mean it just doesn't work?

---

### Post by Didius Falco on 2009-04-26
until they fix the bug. Meanwhile, give "dreamchess" a look. It's 3d and in the repos. I'm playing around with right now.

---

### Post by nverdo on 2009-04-27
check the comment from  xiando: 
[https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/356553/comments/1](https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/356553/comments/1)

worked for me :popcorn:

---

### Post by JK3mp on 2009-04-27
I didn't have any probs with it either. Check out the bug report and see wat the status is on it.

---

