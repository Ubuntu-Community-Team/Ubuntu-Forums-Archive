---
title: "How do I completely remove a user?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by zer010 on 2009-08-06
I would like to know how to COMPLETELY remove a user from Ubuntu 9.04.  I have tried using the GUI "Delete User" in the Admin> Users and Groups, but if I try to create a user with the same name as deleted I get a message saying that user already exists.  I even went into the filesystem, found that users Home folder and deleted it, but still it says the user exists!  I've tried looking for ways, but couldn't find any solutions suitable.  Any help would be appreciated.

---

### Post by Paddy Landau on 2009-08-06
Here is how I would go about it.

[LIST=1]
[*]System > Administration > Users and Groups > Unlock
[*]Select the username > Delete
[*]Manage Groups > find the group with the same username > Delete
[*]Delete the entire user's directory: sudo rm -r /home/username
[/LIST]

---

### Post by ptn107 on 2009-08-06
```
deluser --remove-home --remove-all-files <username>
```

---

### Post by Jimleko211 on 2009-08-06
```

sudo userdel -f -r xname

```where xname is the name of your user.

---

### Post by Paddy Landau on 2009-08-07
> **Jimleko211 said:**
> sudo userdel -f -r xname
"On Debian, administrators should usually use **deluser**(8) instead."

---

### Post by zer010 on 2009-08-08
Thanks for the info! I think I probably missed deleteing the user group.  Thanks!

---

### Post by colau on 2009-08-08
> **zer010 said:**
> Thanks for the info! I think I probably missed deleteing the user group.  Thanks!
Mark your thread as solved.

---

