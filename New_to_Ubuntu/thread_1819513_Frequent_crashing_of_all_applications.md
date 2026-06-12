---
title: "Frequent crashing of all applications"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by msidhard on 2011-08-06
Hi friends,
     Am using ubuntu 11.04 on pentium 4 with 1GB DDR1 ram and now I upgraded to celeron D processor with DDR2 512MB ram. there was no issue when i was using with p4, this issue came up only after upgrading. My applications like firefox, chromium, Libre office crashes often so that I cant use the system at all. Chromium sometime seems to be stable. when i use java enabled site or flash enabled sit suddenly the browsers crashes. i cannot switch to full screen in flash player. totally saying my system seems to be unstable.

---

### Post by vanadium on 2011-08-06
You have a relatively limited amount of RAM. The behaviour you describe could be due to the absence of swap space. In that case, the system has to stop processes abruptly if it is running out of physical memory.

Check whether you have swap, and whether the swap is in use with the command

```

free

```

or either one of

```

cat /proc/swaps
swapon -s

```

---

