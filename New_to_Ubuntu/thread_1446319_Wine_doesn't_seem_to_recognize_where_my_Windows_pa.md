---
title: "Wine doesn't seem to recognize where my Windows partition is"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Masterion on 2010-04-03
Title.

Specifically, when configuring Wine to try to find my Windows partition, it isn't regonized. Any help on this?

---

### Post by Bradtek on 2010-04-03
Is your Windows Partition mounted ?

Wine installs windows programs to 
/home/.wine/
(Something like that I don't have it installed)

---

### Post by yetiman64 on 2010-04-03
1st the windows partition has to be mounted in linux (is it?)

Open configure Wine, then on the Drives tab, use add , browse to the folder in linux that has windows mounted, eg /media/<windows mount folder>, click apply and the windows folder in linux is given a drive letter under wine. Just checked this on my wine install and it worked.:) hope it helps.

> Wine installs windows programs to 
/home/.wine/Yes that's right.

---

