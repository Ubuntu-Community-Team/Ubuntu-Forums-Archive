---
title: "Group permissions"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by ash369 on 2010-07-23
I have just made a new user and group on ubuntu. What i want to do is add a permission on the new group which will allow any user in that group to execute.

The group i made is called owner and the user is called srcds1, this is how it appears in the group file.

```
srcds1:x:1002:
owner:x:1003:
```

How do i set the permission to the owner group to allow execute? And how would i add the user to that group?

---

### Post by Bachstelze on 2010-07-23
> **ash369 said:**
> I have just made a new user and group on ubuntu. What i want to do is add a permission on the new group which will allow any user in that group to execute.


To execute what?

---

### Post by matrixblue on 2010-07-23
The Read Write and Execute Permissions exist on the files. You would have to configure those persmission either by the file or directory

---

### Post by ash369 on 2010-07-23
The file i'm trying to execute is called srcds_run, so how would i change the permissions on that file?

---

### Post by Bachstelze on 2010-07-23
> **ash369 said:**
> The file i'm trying to execute is called srcds_run, so how would i change the permissions on that file?

[font=monospace]chmod +x srcds_run[/font] in a terminal, or by checking the appropriate box in the properties panel in Nautilus.

---

### Post by ash369 on 2010-07-25
Thanks, i fixed this now.

---

