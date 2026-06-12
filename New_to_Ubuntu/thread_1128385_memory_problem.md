---
title: "memory problem"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by gkraju on 2009-04-17
hi i am having ubuntu 8.04 (Wubi installation) and i am new to linux
i noticed today when i booted memory consumption is 250 Mb
but after 3 hours even though i closed all applications memory consumption is 500 Mb .and memory consumption goes on increasing ..
is this normal behavior or some thing wrong with my system
configuration:
1 GB Ram ,Intel dual core 1.8GHz
thanks in advance

---

### Post by Mac_D83 on 2009-04-17
It's completely normal. Most of it is probably taken up by caching. Linux makes sure to keep files recently read in RAM. This way programs start faster if you open them again. Linux removes those files again from the RAM when it needs it for something else. This way your RAM is constantly used and less is wasted idling.

---

