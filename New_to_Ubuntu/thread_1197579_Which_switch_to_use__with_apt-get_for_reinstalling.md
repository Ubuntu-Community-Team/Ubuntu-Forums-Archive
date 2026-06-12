---
title: "Which switch to use  with apt-get for reinstalling software?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by bhadotia on 2009-06-26
So which switch was it? I thought it was apt-get install -f, but that does not reinstall a package.

---

### Post by mc4100 on 2009-06-26
> **bhadotia said:**
> So which switch was it? I thought it was apt-get install -f, but that does not reinstall a package.

An "aptitude reinstall" will do it.

---

### Post by drs305 on 2009-06-26
Or if you use apt-get:
```

sudo apt-get install --reinstall *packagename*

```
Example: 
sudo apt-get install --reinstall *gimp*

---

### Post by bhadotia on 2009-06-26
> **mc4100 said:**
> An "aptitude reinstall" will do it.

Thanks :D

---

### Post by bhadotia on 2009-06-26
> **drs305 said:**
> Or if you use apt-get:
```

sudo apt-get install --reinstall *packagename*

```
Example: 
sudo apt-get install --reinstall *gimp*

Thank you for the info:popcorn:

---

