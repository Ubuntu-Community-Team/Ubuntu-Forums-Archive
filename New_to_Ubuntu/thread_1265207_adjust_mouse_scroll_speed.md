---
title: "adjust mouse scroll speed"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by kpholmes on 2009-09-13
is there a way i can customize the speed of the scroll wheel on my mouse? its currently really fast. haha. thanks :D

---

### Post by Malta paul on 2009-09-13
This may help:
System>preferences>Mouse 
:D

---

### Post by Lampi on 2009-09-13
or you use xset (man xset) to configure mouse acceleration.

---

### Post by kpholmes on 2009-09-13
where can i get or modify xset?

---

### Post by Lampi on 2009-09-17
sorry for the delay...

> **kpholmes said:**
> where can i get or modify xset?

xset is already installed - you modify mouse acceleration like this:
```
xset mouse <acceleration> <acceleration threshold>
```
see "man xset" for the details

After you found a good setting, you put the xset call into autostart (gnome,kde) or you create/edit your ~/.xsession file (again: see "man xsession" for details)

---

