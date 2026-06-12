---
title: "Reinstalled GRUB, 2nd user no longer valid"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by ovid9 on 2010-01-30
Alright, I just reinstalled GRUB, but I don't think I did it the most efficient way.  However, I don't have to boot of a CD anymore.

However, i have 2 users on my computer, we'll call them a & b.

a is primary user, also has access to root, etc.

b is secondary user.  doesn't have full access.

Both still have their home directories, however user 2 doesn't exist anymore at login.  I tried the old name & password and no luck.

When I tried to add a user b, it says that user already exists because there is a home directly for user b already.   

How do i get it so user b is available again?

---

### Post by Leppie on 2010-01-30
try from the cli:
```
sudo useradd <username>
```

---

### Post by ovid9 on 2010-01-30
Thanks!  That was simple enough.  I ran that, then ran ```
 sudo passwd username 
```

and i'm back in!  

I really need to start learning more terminal stuff.

---

### Post by Leppie on 2010-01-30
glad you're up and running again ;)

---

