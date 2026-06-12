---
title: "Killall --older-than"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Cadeyrn on 2010-10-16
It's ridiculous that there's no decent documentation on this. After Googling for hours, all I can find is it follows the format s,m,h,d,w,M,y. But typing all those numbers in separated by a comma won't work. How the hell do I kill all processes older than 30 minutes???

Of course I don't mean ALL processes. Just the ones with a certain name.

---

### Post by yetiman64 on 2010-10-16
To kill a recently started multiple instance of a process (leaving the latest one) this works (finally hit the right time format when testing on fusion-icon)

```
killall --older-than 30m <process-name>
``` If you wanted 1 hour 30 minutes it looks like,

```
killall --older-than 30m,1h <process-name>
``` tested this on tomboy notes and it worked as well (tomboy notes only allows one instance so started a new one and tested the command again and it left the newly opened one alone).

---

### Post by Cadeyrn on 2010-10-16
Thanks.

---

