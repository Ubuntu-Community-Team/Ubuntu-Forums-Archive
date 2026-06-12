---
title: "Segmentation faulty tree"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by gregarion on 2010-01-27
Hey guys , im getting a segmentation faulty tree when i try to install a package from the terminal. what can be the problem?

---

### Post by J V on 2010-01-27
Don't double post

(And the rest of you looking at this, don't feed the... whatever)

---

### Post by paul_in_london on 2010-01-27
Run this command:

```
sudo rm -vf /var/cache/apt/*.bin
```

and then try to install your package again.

---

