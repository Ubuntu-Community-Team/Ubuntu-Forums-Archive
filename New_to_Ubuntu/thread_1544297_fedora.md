---
title: "fedora"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by pgolphin on 2010-08-02
If i delete the /etc/aliases file, how can i re-create it even if i haven't restarted sendmail?

---

### Post by uRock on 2010-08-02
vi /etc/aliases will create the file, but you will have to be logged in as root to write in that folder.

Cheers,
uRock

---

### Post by pgolphin on 2010-08-02
ok i see what you are saying, does this also apply in ubuntu?

---

### Post by uRock on 2010-08-02
vi is short for visual editor. When you give it a command to open a file, it looks for it and when it doesn't see the file there, then it creates a new one. This doesn't mean it will work. It just creates an empty file, unless you write in it.

---

