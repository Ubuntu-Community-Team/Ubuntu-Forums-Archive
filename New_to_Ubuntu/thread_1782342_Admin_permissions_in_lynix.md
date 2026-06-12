---
title: "Admin permissions in lynix"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Larryrl on 2011-06-14
[SIZE=3]Why is ity with Abuntu and most Abuntu dirivitives, as well as some other lynix distributions, I get it installed and want to move some ttf fonts over to usr/share/fonts, and it tells me I do not have permission to copy to that folder even thought I am setup as admin?[/SIZE]

---

### Post by Elfy on 2011-06-14
Because /usr doesn't belong to you (the user).

You need to move them as root - you can use nautilus as root - carefully.

```
gksudo nautilus
```

/home/youruser belongs to you

/home/another user doesn't

---

