---
title: "[SOLVED] Why does 'echo $shell' display blank screen?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by pet_the_ibex on 2008-12-03
I am running intrepid (8.10) on a live CD, and the echo command is working strangely. If I type 'echo $shell' or certain other commands where text output should be displayed, nothing but a blank line is printed. Could the reason for this be that I am running from a disk, and not from a full installation?

Thanks,
-Lee

---

### Post by kpkeerthi on 2008-12-03
```
echo $SHELL
```
The variable is case-sensitive.

---

### Post by pet_the_ibex on 2008-12-03
Thank you so much!!

How embarrassing. :)

---

