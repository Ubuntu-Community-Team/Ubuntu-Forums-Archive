---
title: "Not able to save downloads file after auto updating 9.04 Jaunty"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by putush on 2009-08-20
I am using Jaunty 9.04. Today after an auto-update prompt the following packages were downloaded:

libgnutls26 (2.4.2-6) to 2.4.2-6ubuntu0.1
linux-headers-2.6.28-15 (2.6.28-15.48) to 2.6.28-15.49
linux-headers-2.6.28-15-generic (2.6.28-15.48) to 2.6.28-15.49
linux-image-2.6.28-15-generic (2.6.28-15.48) to 2.6.28-15.49
linux-libc-dev (2.6.28-15.48) to 2.6.28-15.49

After doing that a peculiar problem has developed, I am not able to download anything from the net. Specifically I cannot save any file. The problem is not limited to any specific file type. Both Firefox and Opera has been affected. Plus even when I do a simple text copy from the net and try to save it through TextEdit it freezes and goes gray. I thought of removing these updates, but there are too many dependencies and I just didn't know, how to roll back the changes and if at that might help. Any help would be appreciated... thanks a ton in anticipation.

---

### Post by jrox717 on 2009-08-20
Well, those files are a new kernel that was installed. When you boot up, you will see text in the corner of the screen that says "Press esc to enter menu". In the menu, select "Ubuntu 9.04, kernel 2.6.28-14-generic" instead of "2.6.28-15-generic" and see if that makes a difference.

---

### Post by x33a on 2009-08-20
boot into a different kernel as jrox said.

and, also try downloading through wget.

---

### Post by putush on 2009-08-21
Hi, I did that but the problem is still persisting. Infact, it is developing right after I have used my browser for about 3 mins or so.When i look into the system monitor, it shows my browser has gone into a "hrtimer nanosleep". After about 3-5 mins of freezing, the browser finally proceeds to download and unfreezes on its own.

---

