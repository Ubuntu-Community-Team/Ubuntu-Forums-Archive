---
title: "Package cache problem"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-04-10
E: The package cache file is corrupted
E: _cache->open() failed, please report.

How do I go about fixing this?

Thanks.

---

### Post by Gerwin on 2009-04-10
When i remember correctly restarting the system will help. because the cache would be cleaned. I'm not sure but trying can't hurt.

---

### Post by Michael.Godawski on 2009-04-10
hi dunbrokin,

 Which program produces this output?

Try to run these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --reconfigure -a
```

---

### Post by dunbrokin on 2009-04-10
> **Gerwin said:**
> When i remember correctly restarting the system will help. because the cache would be cleaned. I'm not sure but trying can't hurt.

Thanks ...that worked...

---

