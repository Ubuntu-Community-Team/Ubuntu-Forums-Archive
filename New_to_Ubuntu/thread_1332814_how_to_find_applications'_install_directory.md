---
title: "how to find applications' install directory"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by infestor on 2009-11-20
let's say i would like to know in which dir totem or firefox is installed? how do i do that? is there a console command for that?

---

### Post by NoaHall on 2009-11-20
locate firefox | grep bin
They'll mostly be inside /usr/bin/

---

### Post by diesch on 2009-11-20
```
dpkg -L somepackage
``` shows you the files belonging to the package *somepackage*

---

### Post by Ryadt on 2009-11-20
> **NoaHall said:**
> locate firefox | grep bin
They'll mostly be inside /usr/bin/
Or ```
whereis firefox
```

---

### Post by infestor on 2009-11-20
> **NoaHall said:**
> locate firefox | grep bin
They'll mostly be inside /usr/bin/

> **diesch said:**
> ```
dpkg -L somepackage
``` shows you the files belonging to the package *somepackage*

> **Ryadt said:**
> Or ```
whereis firefox
```

awesome! thansk a lot guys! *woop* *woop*

---

### Post by zacktu on 2009-11-20
On the command line "whereis firefox" will show you all of the files named firefox.  For me they are

/usr/bin/firefox /usr/lib/firefox /usr/share/firefox

The command "which firefox" shows the executable.  For me that is 

/usr/bin/firefox

---

