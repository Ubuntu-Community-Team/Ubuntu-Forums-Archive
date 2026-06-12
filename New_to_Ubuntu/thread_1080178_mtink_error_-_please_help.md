---
title: "mtink error - please help"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by kapi on 2009-02-25
Hi, have installed the mtink but when trying to run the application I get an error message saying no access to printer device file and that in debian systems like ubuntu I ave to configure so that I am part of a lp group.

Would very much appreciate some help please

Kindest regards

Kapi

---

### Post by llamabr on 2009-02-25
Hi.  You might get better results if you take this to the appropriate forum.  I assume there's a printer forum here, where people know more about these things.

---

### Post by prinny42 on 2009-02-25
I haven't had this problem before, as I've never used mtink, but if being added to the lp group is all that's necessary, that's easy enough.

```
sudo usermod -aG lp
```

EDIT:  Sorry, that's wrong.  It should be
```
sudo usermod -aG lp (Your Username)
```

---

