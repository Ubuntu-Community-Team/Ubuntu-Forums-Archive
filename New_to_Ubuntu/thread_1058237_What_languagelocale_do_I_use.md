---
title: "What language/locale do I use?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-02-02
I have a package that is confused by the language/locale. I can't find these settings in System/Pref or Admin.

Where are these? How can I edit them?

---

### Post by jimmy the saint on 2009-02-02
What package is confused and what is the error message you are getting?

---

### Post by Mark_in_Hollywood on 2009-02-02
mark@Lexington-19:~/gourmet-0.14.3$ gourmet
Traceback (most recent call last):
  File "/usr/bin/gourmet", line 13, in <module>
    from gourmet.OptionParser import *
  File "/usr/lib/python2.5/site-packages/gourmet/__init__.py", line 14, in <module>
    import keymanager
  File "/usr/lib/python2.5/site-packages/gourmet/keymanager.py", line 3, in <module>
    from defaults import **langProperties as langProperties**
ImportError: cannot import name langProperties

The author of this program asks me what language/locale I'm "in".

---

### Post by jimmy the saint on 2009-02-06
I did a little research and it seems that "gourmet" has some known bugs with internationalization.  I found two seperate bugs, both of which refer to crashes involving localization, which seems to be what you are experiencing.  Are you using english?  I think it is likey a bug in the package, rather than an issue with Ubuntu.  You could try to compile it yourself if you want to go that route, that may work.  Definitely file a bug though, and include the infomation you posted here.  Sorry I couldn't be more help.  Hopefully someone with more guru powers sees this and shares a brilliant solution!

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1236213.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1236213.html)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507382](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507382)

Edit one more link:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1947796&group_id=108118&atid=649652](http://sourceforge.net/tracker/index.php?func=detail&aid=1947796&group_id=108118&atid=649652)
That's where you should file the bug.

---

