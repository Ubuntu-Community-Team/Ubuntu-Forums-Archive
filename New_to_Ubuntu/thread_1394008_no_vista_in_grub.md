---
title: "no vista in grub"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by iRounak on 2010-01-30
I installed ubuntu karmic on a friend's laptop using the karmic dvd. He had vista in c:\. i installed ubuntu in d. Grub does not show vista. Only ubuntu can be started. what to do now?

---

### Post by garvinrick4 on 2010-01-30
> **iRounak said:**
> I installed ubuntu karmic on a friend's laptop using the karmic dvd. He had vista in c:\. i installed ubuntu in d. Grub does not show vista. Only ubuntu can be started. what to do now?

Try to open a Terminal and type in CODE:

        sudo update-grub

If that does not work use this link to read on fix.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Updating grub should work.

D: drive in Vista was the recovery at install wasn't it?

---

### Post by kansasnoob on 2010-01-30
> **iRounak said:**
> I installed ubuntu karmic on a friend's laptop using the karmic dvd. He had vista in c:\. i installed ubuntu in d. Grub does not show vista. Only ubuntu can be started. what to do now?

If simply running "sudo update-grub" fails to find it then we should see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

