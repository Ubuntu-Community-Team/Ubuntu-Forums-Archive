---
title: "adding gimp plug-ins"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by furoido on 2010-06-08
Want to add a vignette plug-in for gimp. I downloaded a file onto my desktop (vignette_0.scm), but haven't got a clue how to install it in gimp!! Anybody be kind enough to take me step-by-step through the process?

---

### Post by SlidingHorn on 2010-06-09
open a terminal and move the file to the scripts directory:

```
sudo mv /home/<yourusername>/Desktop/vignette_0.scm /usr/lib/gimp/2.0/scripts/
```

---

