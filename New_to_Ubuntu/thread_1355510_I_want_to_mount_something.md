---
title: "I want to mount something"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-15
:::Ahem::: Scuze the title, but, it made ya click.  I don't have an external anything, and am working in my Linux book about mounting files systems.  What can I mount for practice?  Any ideas?  Hopefully, and suggestions will have a negligible impact on my system.  I'm new and am trying to keep it safe.

Thanks,
-Diametric

---

### Post by llamabr on 2009-12-15
```
sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test
cd /mnt/test
ls
sudo umount /mnt/test
```

You'll even get an informative error.

---

### Post by myolbug on 2009-12-15
Don't we all, son.  Don't we all!!!

Thanks for bringing this up, I may be able to use it with my computer...

---

### Post by longtom on 2009-12-15
> **myolbug said:**
> Don't we all, son.  Don't we all!!!


What do you mean, cowboy....:D:D:D

---

