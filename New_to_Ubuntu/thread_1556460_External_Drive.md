---
title: "External Drive"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by nkingcade on 2010-08-19
I have a 500gB WD external hard drive. I just reloaded Ubuntu 10.04. The external drive shows up as a long number (204c1aaa-751a-4071-8b8f-17a68829e84f)When I attempt to change file access permissions and the execution permission, the permission and check box are selectable. But change to nothing when I close. Is there documentation for administering permissions for these devices or am I missing something?

---

### Post by blazemore on 2010-08-19
Try pressing Alt+F2 and typing in
```
gksu nautilus
```

Then press Enter.

Put in your password, and then you'll have a file browser with administrative privelages. From here you can do almost anything, including changing permissions on this hard disk.

---

