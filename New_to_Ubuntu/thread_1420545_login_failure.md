---
title: "login failure"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-03-03
i deleted all accounts by mistake and when i login its showing login failure so is there any way to solve it??

---

### Post by 1991sudarshan on 2010-03-03
> **1991sudarshan said:**
> i deleted all accounts by mistake and when i login its showing login failure so is there any way to solve it??dda

---

### Post by alexandari on 2010-03-03
Have you tried logging in as root?

---

### Post by nothingspecial on 2010-03-03
Boot into recovery shell
```

useradd new_account admin
``` to create a sudo account then

```
usermod -G adm,dialout,cdrom,audio,fuse,plugdev,admin -a new_account
```

---

