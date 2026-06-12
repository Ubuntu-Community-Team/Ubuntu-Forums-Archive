---
title: "user not in sudoers file, this incident will be reported"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by AlphaWhelp on 2009-12-15
Where do I go to find this report of people who have tried to perform an unauthorized sudo?

---

### Post by Bucky Ball on 2009-12-15
I think you may have just typed the wrong password in a terminal. Don't sweat it.

---

### Post by sandyd on 2009-12-15
/var/syslog
its burried in that huge pile of stuff.

---

### Post by AlphaWhelp on 2009-12-15
Thanks

---

### Post by jamesrl on 2010-12-29
I don't see it in /var/log/syslog in 10.04, but now see it in /var/log/auth.log (along with other su/sudo material).  Looked due to [http://xkcd.com/838/](http://xkcd.com/838/) comic and found this link, and then just grepped for it in /var/log finding it only in auth.log.

---

### Post by uRock on 2010-12-29
Necromancy! :twisted:

Thread Closed.

---

