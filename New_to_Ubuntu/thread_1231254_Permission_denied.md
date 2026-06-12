---
title: "Permission denied"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-08-04
hey, trying to put a folder into the file system, but it says that i do not have permission.  what do i need to do?

thanks

---

### Post by drs305 on 2009-08-04
You are probably trying to move a something into a system folder. To do that, you need to have admin powers. Open nautilus with the following command, giving you 'root' capabilities if you have that permission. It will ask you for your password before it opens nautilus:
```

gksudo nautilus

```

This would probably make good reading:
[_RootSudo_]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Elfy on 2009-08-04
sudo I would guess

```
sudo command options
```

You will gain the permissions by using sudo

---

### Post by gwilkins82 on 2009-08-04
great - sudo does the trick - thanks for the info, will read up on it

---

