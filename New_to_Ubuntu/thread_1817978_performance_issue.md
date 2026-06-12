---
title: "performance issue"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Aitashan on 2011-08-04
is it me or dual boot with xp and ubuntu dose make your os slow cuz i  am experiencing a little lag while booting to ubuntu

---

### Post by 3rdalbum on 2011-08-04
It shouldn't be any different from single-boot Ubuntu. Does your System Monitor show any programs using up a lot of CPU time?

Also, if you've installed Ubuntu as dual-boot with Windows and you performed this using Wubi (the installer that runs within Windows), then yes there is a performance penalty. This is because your Linux filesystem is mounted within your Windows one. You can avoid this by doing a real dual-boot installation using the Ubuntu-based installer on the Ubuntu CD.

---

### Post by wildmanne39 on 2011-08-04
Hi, also if you did a normal install and you are using natty then it is normal for it to take a little longer then previous releases, but if you tells us how long it takes we will have a better idea.

Also you can look at your logs with log file viewer and see what is taking a long time to load by looking in the boot log.

---

### Post by Aitashan on 2011-08-04
can i do a real boot installation using startup disk creator

---

### Post by wildmanne39 on 2011-08-04
Hi, after you download ubuntu you can use boot disc creator to make a bootable ubuntu disk or just burn it to disk.

---

