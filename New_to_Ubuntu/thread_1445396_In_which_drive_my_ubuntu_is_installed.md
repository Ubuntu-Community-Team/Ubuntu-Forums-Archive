---
title: "In which drive my ubuntu is installed ?"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by lucky.developer on 2010-04-02
I have installed ubuntu alongside windows using wubi. I want to know the partition in which the ubuntu is installed... how do i check it from ubuntu terminal ?

---

### Post by Elfy on 2010-04-02
Try and see what 

```
df -h 
mount
```

show you

---

### Post by Mark Phelps on 2010-04-02
> **lucky.developer said:**
> I have installed ubuntu alongside windows using wubi. I want to know the partition in which the ubuntu is installed... how do i check it from ubuntu terminal ?

Unless you specifically directed it to use a different partition, by default, it installed inside your Windows OS partition.

---

### Post by The Cog on 2010-04-03
> Unless you specifically directed it to use a different partition, by default, it installed inside your Windows OS partition.
One large file inside the windows partition, I believe.

---

