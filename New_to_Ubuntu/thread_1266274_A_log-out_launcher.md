---
title: "A log-out launcher"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-09-14
Hello,

I'm trying to figure out the launcher equivalent of the "log out" command.  Does anyone know the code I would use in a non-panel launcher?  I don't mind it requiring a password.

Thanks in advance!

-Val

---

### Post by NoaHall on 2009-09-14
Put under the command bit -
```
logout
```

---

### Post by lswb on 2009-09-14
> **Prince Valiant said:**
> Hello,

I'm trying to figure out the launcher equivalent of the "log out" command.  Does anyone know the code I would use in a non-panel launcher?  I don't mind it requiring a password.

Thanks in advance!

-Val

Since you refer to launcher, I'm guessing you mean to log out of gnome desktop session.

To bring up the logout dialog:

gnome-session-save --logout-dialog

To immediately logout without a dialog box:

gnome-session-save --logout

---

### Post by Prince Valiant on 2009-09-15
Thanks iswb.  That's all I needed.  :-D

-Val

---

