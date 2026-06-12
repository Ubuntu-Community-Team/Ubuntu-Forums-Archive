---
title: "root?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by yangt299 on 2009-01-04
On the file system, why is the owner known as "root"? Is there any way to change this?

---

### Post by Bachstelze on 2009-01-04
Change it to what?

---

### Post by taurus on 2009-01-04
Yes, there is a user called root but the account is locked as a default.  If you need root privilege, use sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2009-01-04
> **taurus said:**
> Yes, there is a user called root but the account is locked as a default.  If you need root privilege, use sudo/gksudo.

I don't believe this is relevant to the question asked...

---

### Post by SuperSonic4 on 2009-01-04
It's also known as the Superuser?

---

### Post by albinootje on 2009-01-04
> **yangt299 said:**
> On the file system, why is the owner known as "root"? Is there any way to change this?

It can be changed (by creating another user with uid 0 and then use the chown command), but it is highly recommended to not do that!

Since many many years "root" is the username of the system administrator on Linux systems.

For more information about permissions, read this :
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

