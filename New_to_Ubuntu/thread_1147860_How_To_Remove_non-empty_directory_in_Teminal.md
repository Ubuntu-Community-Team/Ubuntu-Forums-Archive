---
title: "How To Remove non-empty directory in Teminal"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-05-03
Hi,

i am not able to remove a directory which is not empty in the terminal. What command should i use to remove that directory which is not empty .. i want to remove its subfolders and its contents as well?


please help

thanks

---

### Post by nandemonai on 2009-05-03
> **luckydeveloper said:**
> Hi,

i am not able to remove a directory which is not empty in the terminal. What command should i use to remove that directory which is not empty .. i want to remove its subfolders and its contents as well?


please help

thanks

```
rm -r dirname
```

Be careful with that command though, it can cause serious damage if you use it wrong.

If in doubt:

```
man rm
```

Will show the documentation.

---

### Post by luckydeveloper on 2009-05-03
thans :-)

---

