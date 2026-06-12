---
title: "Changeing Time with exiftool"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-06-21
Trying to change a few pictures creation time with exiftool but I'm not very successful so far, what I would like to do is to change all jpg files in dir /home/linux/temp/ creation date from 2007/01/01 to /2009/06/19 but I don't how. Could you please help me?

---

### Post by Celauran on 2009-06-23
Might be easier to do with touch. Navigate to the directory containing the images to be changed, and type this:

```
for i in *; do touch -t 200906191200 "$i"; done
```

This will change the time to noon on June 19.

---

