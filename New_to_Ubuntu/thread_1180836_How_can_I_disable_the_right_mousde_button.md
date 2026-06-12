---
title: "How can I disable the right mousde button?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Igniteflow on 2009-06-07
I've set up an old laptop with Xubuntu for my nephew to use.  It works great and he's seems to enjoy Tuxpaint, but is there a way I can turn off the right mouse button?  He always seems to click it and ends up opening menus when he just wants to paint.

---

### Post by keplerspeed on 2009-06-07
You can use xmodmap to do this. For example, open a terminal, and enter this code:
```

 xmodmap -pp

```

This will list all the pointer buttons, and their 'designated' number. To disable right click we just need to specify the right click button to a number that doesnt do anything. Entering this should do the job:

```

xmodmap -e "pointer = 1 8 9 4 5 6 7 2 3"

```

This will map the buttons #2 and #3 (order in the list. button #2 is usually right click) to a designated number of 8 and 9.

Cheers!

---

### Post by Igniteflow on 2009-06-07
Excellent, thank you!

---

