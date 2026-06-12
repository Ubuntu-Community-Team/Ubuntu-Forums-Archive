---
title: "SH: Calculate time difference in HH:MM"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by honeybear on 2011-07-07
Hello, 

Little question regarding time calc, when bit tricky.
How could it be calculated the time diff between:

22:30 until 6:30 following day = ?  with SH

Any input welcome

---

### Post by Vaphell on 2011-07-07
```

from='2011-12-12 10:36:34'
to='2011-12-14 18:33:58'

fsecs=$( date -d "$from" +%s )
tsecs=$( date -d "$to" +%s )
diff=$(( tsecs - fsecs ))
printf ""%dh:%dm:%ds"\n" $(($diff/3600)) $(($diff%3600/60)) $(($diff%60))

55h:57m:24s

```

---

### Post by honeybear on 2011-11-13
> **Vaphell said:**
> ```

from='2011-12-12 10:36:34'
to='2011-12-14 18:33:58'

fsecs=$( date -d "$from" +%s )
tsecs=$( date -d "$to" +%s )
diff=$(( tsecs - fsecs ))
printf ""%dh:%dm:%ds"\n" $(($diff/3600)) $(($diff%3600/60)) $(($diff%60))

55h:57m:24s

```

Finally  I had time to work on it. Thanks a lot!!

---

