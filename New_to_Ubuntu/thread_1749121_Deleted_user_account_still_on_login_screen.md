---
title: "Deleted user account still on login screen"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by migs73 on 2011-05-04
Hi all

I am running 10.10, and created two new user accounts for testing purposes. I have since deleted these accounts in Users and Groups.

After logging out both accounts still appear on the list of accounts at the login screen. Shutdown and restarted but still they are there. Checked the /home folder but there are no folders there for these users.

Does anybody have any idea of what I can try?



Mike:)

---

### Post by wojox on 2011-05-04
```
sudo usermod -u 999 wojox
```

---

### Post by migs73 on 2011-05-05
Thanks Wojox,

These aren't the droids were looking for........I mean that worked. Don't know what came over me there.  ;)

Mike

---

