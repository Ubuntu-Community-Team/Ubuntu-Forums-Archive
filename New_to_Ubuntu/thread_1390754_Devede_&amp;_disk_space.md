---
title: "Devede &amp; disk space"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by lizandeen on 2010-01-26
I recently asked this question "I have a 500g xp and ubuntu 8.10 dual boot system (169g and 328g respectively) with 2g of ram. The problem is that when I try to create an iso with Devede I'm told "Conversion failed Maybe you ran out of disk space?". Any ideas? Thanks in advance" but unfortunately never got a reply that worked. I have now installed 9.04 (the rest is the same) but still have the same problem-once more, any ideas? Thanks

---

### Post by ThePinkWitch on 2010-01-26
I don't know If you have the same problem I had yesterday, but I got the same message and realised you have to shrink the DVD first. The data on the DVD is too much for the shop bought DVDs so you have to use a program to make it fit on the average disk. You can get DVD shrink for free. Just download it and then use the program, then burn it. I used DVD shrink, then burned with Brasero. Worked great :D  Hope that helps :) I forgot to say install DVD shrink with the program WINE.

---

### Post by inobe on 2010-01-26
> **lizandeen said:**
> I recently asked this question "I have a 500g xp and ubuntu 8.10 dual boot system (169g and 328g respectively) with 2g of ram. The problem is that when I try to create an iso with Devede I'm told "Conversion failed Maybe you ran out of disk space?". Any ideas? Thanks in advance" but unfortunately never got a reply that worked. I have now installed 9.04 (the rest is the same) but still have the same problem-once more, any ideas? Thanks

where is the finished iso being stored ?

use ubuntu's disk analyzer to see what part of your drive is fool.

---

### Post by fooman on 2010-01-26
your disc is probably no wheres near full...it is a bug with devede.  i had the same happen to me and it drove me nuts.

wish i could remember exactly how i fixed it....i believe what i did was uninstalled the ubuntu version and downloaded/installed the latest version from thier website:

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

hope that helps.

---

### Post by lizandeen on 2010-02-04
Thanks for the help. I'm using my desktop to store to and so far- so good!

---

### Post by lizandeen on 2010-02-05
Okay that worked the first two times I tried, now I'm getting the same "ran out" message again. Any more suggestions, because this is becoming incredibly annoying?

---

### Post by lizandeen on 2010-02-15
Bump

---

### Post by mikechant on 2010-02-16
Could you post the output of the 'df' command?

(i.e. Open terminal with ALT+F2, type df, cut and paste output)

---

### Post by stoneheart on 2010-02-16
Believe it or not, I've run into this problem when trying to make more than 1 DVD in quick succession on my modest system.  Rebooting after each DVD creation seems to make the problem go away.

I know, I know.  What can I say?

---

### Post by lizandeen on 2010-02-18
Here's what came up when I put in the "df" command:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            317756204  89403916 212338296  30% /
tmpfs                   480480         0    480480   0% /lib/init/rw
varrun                  480480       220    480260   1% /var/run
varlock                 480480         0    480480   0% /var/lock
udev                    480480       180    480300   1% /dev
tmpfs                   480480         0    480480   0% /dev/shm
lrm                     480480      2192    478288   1% /lib/modules/2.6.28-18-generic/volatile
Hope this sheds some light on the problem, in the meantime I'll try the rebooting method. Thanks

---

### Post by lizandeen on 2010-03-01
bump again

---

