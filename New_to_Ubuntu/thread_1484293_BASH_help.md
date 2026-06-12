---
title: "BASH help"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Kafubie on 2010-05-15
Let's say if I have a file on my desktop that does have a file name called "derp derp"
If I wanted to delete the so called "derp derp" I would have to rename it to "derpderp.jpg" or any file extensions..

How would I be able to delete a file with spaces and no file extension?

I just got into bash like couple days ago and so far getting familiar with it.  It's fun!

blah@blah-Laptop~$ cd Desktop
nathaniel@nathaniel-laptop:~/Desktop$ rm derp derp

WHAT I DO?!

---

### Post by patchwork on 2010-05-15
```
rm derp\ derp
rm 'derp derp'
rm "derp derp"
```

Any of those should work

The \ is an escape character to escape the space

---

### Post by Kafubie on 2010-05-15
> **patchwork said:**
> ```
rm derp\ derp
rm 'derp derp'
rm "derp derp"
```

Any of those should work

The \ is an escape character to escape the space

Thanks man.

---

