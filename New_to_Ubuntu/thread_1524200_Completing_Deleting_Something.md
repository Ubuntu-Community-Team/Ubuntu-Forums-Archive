---
title: "Completing Deleting Something"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by JP121 on 2010-07-04
Hi.

So I feel dumb because I have seen this before, but what is the command you use to completely delete and application, like VirtualBox?

Thanks.

---

### Post by BlazeFire247 on 2010-07-04
You can use the Ubuntu Software Center to uninstall it.

---

### Post by Darkness Des on 2010-07-04
```

sudo aptitude purge virtualbox-ose

```

---

### Post by lkjoel on 2010-07-04
```
sudo apt-get remove --purge (your package name)
```

---

### Post by JP121 on 2010-07-04
Thankyou!

---

### Post by lkjoel on 2010-07-04
If it does work, you should mark this thread as solved.

---

