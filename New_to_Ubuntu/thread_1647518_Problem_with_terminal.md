---
title: "Problem with terminal"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by bj218 on 2010-12-17
I do not know what I did but while in terminal I did something that changed
the size of the display from about 4"x 3" to something quite large. Now I am unable to do anything to close terminal. Is there a way to fix my problem?

---

### Post by NCLI on 2010-12-17
> **bj218 said:**
> I do not know what I did but while in terminal I did something that changed
the size of the display from about 4"x 3" to something quite large. Now I am unable to do anything to close terminal. Is there a way to fix my problem?

alt+F4 ?

---

### Post by hwychld on 2010-12-17
Type: exit

That will close the terminal.  Next time you open a terminal it should be the correct size.  If not, post again.

---

### Post by karthick87 on 2010-12-17
Press **ALT+F2**,and type the following..

```
gconftool --recursive-unset /apps/gnome-terminal
```

---

### Post by bj218 on 2010-12-17
> **NCLI said:**
> alt+F4 ?

That did it THANKS

---

### Post by cgroza on 2010-12-17
You could also use Alt+ Mouse to move the window a little bit so you can click the X.

---

