---
title: "no sund on 9.10"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by gfather6 on 2009-11-16
Need help with 
from term window type alsamixer, then graphics comes up with my internal sound  card.. 
how do I type in alsamixer command to get my other card to come up on graphics to see its settings.

---

### Post by nathan726 on 2009-11-17
It is far easier to right-click the sound icon in the panel and modify the volume from there.
But since you asked...

```
alsamixer -c n
```Replace "n" with a number: 0 is first card, 1 is the second sound card, 2 is the third and so on.
(for more info you can run "info alsamixer", press "q" to quit)

---

