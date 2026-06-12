---
title: "best way to remove user"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-01-07
what is the best way to completely remove a user. note i have a separate home partition if this makes a difference/.tks

---

### Post by blind2314 on 2011-01-07
```
userdel -r <username>
```

---

### Post by seawolf167 on 2011-01-07
[URL="https://help.ubuntu.com/10.04/serverguide/C/user-management.html"]Ubuntu User Management
[/URL]

---

### Post by nothingspecial on 2011-01-07
> **blind2314 said:**
> ```
userdel -r <username>
```

Add the -f option and they are gone, logged in or not. :evil:

---

### Post by rburkartjo on 2011-01-07
not, tks that did the trick

---

