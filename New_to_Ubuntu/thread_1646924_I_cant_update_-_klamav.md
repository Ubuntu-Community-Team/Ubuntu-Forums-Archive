---
title: "I cant update - klamav"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by yae7 on 2010-12-16
Hi

I can not update klamav 9.6. I have followed the steps of this topic:
[http://ubuntuforums.org/showthread.php?t=1547713&highlight=update%2Bklamav](http://ubuntuforums.org/showthread.php?t=1547713&highlight=update%2Bklamav)

 but my problem continues.

if i try to update via consola:

> Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
QLayout "unnamed" added to Klamav "KlamAV ", which already has a layout
Error: "/tmp/ksocket-elmeuusuari" is owned by uid 1000 instead of uid 0.
elmeuusuari@elmeuusuaripc:~$ Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.

any help? 

thanks in advance

---

### Post by Wobblybob on 2010-12-18
the error message is saying that you own the folder /tmp/kde-elmeuusuari not root [root uid =0 your uid=1000] so you need to change the ownership with this;

Open a Terminal and type;

sudo chown root.root /tmp/kde-elmeuusuari

this gives root ownership of the folder.

---

