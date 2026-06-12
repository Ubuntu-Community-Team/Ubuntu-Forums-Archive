---
title: "Clear Screen Behaviour of man Command"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by PointyWombat on 2009-07-02
Hi all,

Just wondering how I can control the behaviour of the man command in a terminal so that it does not clear the man page text when I quit it.  This is a big pet peeve of mine.

Thanks,

---

### Post by decoherence on 2009-07-02
Try putting

```
export LESS='-X'
```

in your .bashrc or .profile

---

### Post by Mornedhel on 2009-07-02
Whuokay, the previous poster has a much better idea than my ugly workaround.

---

### Post by PointyWombat on 2009-07-02
Awesome.. Thanks decoherence.

---

