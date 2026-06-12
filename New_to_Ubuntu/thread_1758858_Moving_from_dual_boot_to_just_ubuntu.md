---
title: "Moving from dual boot to just ubuntu"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by adr9 on 2011-05-15
sorry if this has already been addressed elsewhere on the forum, but I'm guessing it's a really simple problem to solve; I searched on the forums, but everything similar to this request had extra complications that I just don't have.
So, I have a laptop dual booted with windows and ubuntu, and now I simply want to remove windows and have ubuntu as the sole operating system. I really don't want to have to reinstall ubuntu from scratch, but keep what is already there. Is it as simple as just deleting the windows partition? What steps do I need to take? Thank you in advance, for anyone who can help!

---

### Post by JRV on 2011-05-15
It's simple.

Delete the Windows partition.
Create an empty partition to recover the disk capacity.
Run ```
sudo update-grub
```
to remove Windows from the grub boot loader.

---

### Post by ajgreeny on 2011-05-15
If this was a wubi dual boot, ie ubuntu within windows you will probably find it easiest to re-install, though it is possible to move the wubi to a proper partitioned install..

See **[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)** if this is the case.

---

