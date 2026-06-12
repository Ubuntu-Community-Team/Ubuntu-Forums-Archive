---
title: "How to turn on the GUI"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by aagavin on 2009-04-02
I disabled the Graphical login through the services menu and now I don't know how to get it back

---

### Post by Dedoimedo on 2009-04-02
Hello,

When you get to the command line and login, does startx help you get back into the GUI?

Alternatively, try this (sudo) /etc/init.d/gdm start

Cheers,
Dedoimedo

---

### Post by 3rdalbum on 2009-04-02
```
sudo gdm
```

Does the job. First thing you should do is turn "gdm" back on in Services.

---

