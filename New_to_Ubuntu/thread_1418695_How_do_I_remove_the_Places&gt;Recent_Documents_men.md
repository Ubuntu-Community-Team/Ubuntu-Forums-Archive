---
title: "How do I remove the Places&gt;Recent Documents menu?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by diablo75 on 2010-02-28
EDIT:  The command below just took effect.  It didn't appear to work at first, but after logging off and on, then waiting a couple minutes, it worked.!

```
chmod 400 ~/.recently-used
```

---

### Post by NullHead on 2010-02-28
Well okay then. :popcorn:

---

### Post by Baneblade on 2010-02-28
Great. Don't forget to mark this thread as solved then ;)

---

### Post by gacl on 2011-03-03
user@user:~$ chmod 400 ~/.recently-used
chmod: cannot access `/home/gus/.recently-used': No such file or directory

Doesn't work. I guess because I have a different version of Ubuntu?


Gus

---

