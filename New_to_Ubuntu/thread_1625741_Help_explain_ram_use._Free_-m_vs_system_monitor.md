---
title: "Help explain ram use. Free -m vs system monitor?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by weasel fierce on 2010-11-19
Not sure I am understanding properly what I am looking at, so forgive my ignorance.

At the moment, system monitor shows about 460-470 megs of RAM being used.

If I do free -m, it shows 1156 megs being used and 467 in cache, 140 in buffers

What would cause the difference or am I reading things wrong?


Im sure nothing is wrong, Im just curious as to how this works exactly.

---

### Post by cariboo on 2010-11-19
```
 free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1509        499          0         29        855
-/+ buffers/cache:        623       1384
Swap:         1906          0       1906
```

In the example above used memory is the memory you are using at the moment plus, programs that have been cached in ram, that you might use at a later time. For instance if you start-up Firefox, than close it, the next time you start it, it will start noticeably faster.

-/+ buffers/cache, is the actual ram you are using plus the free space left in ram.

---

### Post by weasel fierce on 2010-11-19
> **cariboo907 said:**
> ```
 free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1509        499          0         29        855
-/+ buffers/cache:        623       1384
Swap:         1906          0       1906
```

In the example above used memory is the memory you are using at the moment plus, programs that have been cached in ram, that you might use at a later time. For instance if you start-up Firefox, than close it, the next time you start it, it will start noticeably faster.

-/+ buffers/cache, is the actual ram you are using plus the free space left in ram.

ah I see. In that case, it makes total sense.

---

