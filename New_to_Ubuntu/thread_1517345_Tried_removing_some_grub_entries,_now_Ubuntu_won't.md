---
title: "Tried removing some grub entries, now Ubuntu won't start"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by flyver on 2010-06-24
I followed the steps in [this post]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/").

Removed all of them except the newest one, but now the grub list is exactly the same except I can't start Ubuntu (9.10)!!!

With an installation disk, I guess I can access things, so how can I add them back, those files?

Thank you!

---

### Post by VH-BIL on 2010-06-24
Try
```
sudo update-grub2
```

---

### Post by flyver on 2010-07-09
That actually didn't help - but I somehow managed to fix things after several days of trying. Anyway, that computer now has 10.04.

---

