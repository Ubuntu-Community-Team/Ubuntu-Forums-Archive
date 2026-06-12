---
title: "completely hide panels"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by djyoung4 on 2009-10-01
so in my gnome desktop i want to have the panels completely hide until mouse over.  I have them set to autohide right now but there is still a little bit that sticks out.  how do i make it completely hide.

---

### Post by lisati on 2009-10-01
Right-click on the panel, then click on properties, make sure that "autohide" is selected, and click on "close".

---

### Post by djyoung4 on 2009-10-01
i already have that set but when it autohides there is still a little bit poking out.  how do i make it completely disappear until mouse over

---

### Post by whitethorn on 2009-10-01
the options are in gconf-editor.  I think it's somewhere under apps desktop panels.  I'm not on ubuntu at the moment so I can't check it, in there you can also change the speeds for autohide.

---

### Post by nothingspecial on 2009-10-01
Press Alt+F2

type

```
gconf-editor
```

Go apps > panel > toplevels and choose your panel.

Set the auto_hide_size to 0 

That may not work from memory, it might have to be 1

Not using gnome at the moment so I can`t check.

Anyway, that`s how you do it, have a go.

---

### Post by djyoung4 on 2009-10-01
found it thanks whitethorn

---

