---
title: "is there anything like &quot;run as&quot; in ubuntu to run a program as another user?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by legolas_w on 2010-06-24
I am wondering whether exist anyway to run a program under another user space. 

for example the program is owned by james and james wants to run execute the program under alice user.

is that do-able?

---

### Post by Brandon Williams on 2010-06-24
```
sudo -u alice command
``` will work, provided that james is configured to be allowed to run as command alice.

---

### Post by gmargo on 2010-06-24
If the command is a graphical program, the other user may not have permission to access the display.  Use the **xhost(1)** command to adjust those permissions.

---

