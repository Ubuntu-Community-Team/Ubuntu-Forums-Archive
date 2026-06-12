---
title: "Ndiswrapper commands ERROR"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by pappapump on 2007-06-03
I used ndiswrapper but installed the wrong driver twice.
Now I can't remove either of them with the console
It says to use the command ndiswrapper -r, then the driver name.
I use that and type in the name of the offending driver but it always says locl incorrect etc.
Does anybody know exactly how to type that particular command to remove the wrong driver?

---

### Post by spd106 on 2007-06-04
You will have to use sudo in order to have the access rights.

The other way to achieve the same results is to delete the driver named directory under /etc/ndiswrapper/.

---

