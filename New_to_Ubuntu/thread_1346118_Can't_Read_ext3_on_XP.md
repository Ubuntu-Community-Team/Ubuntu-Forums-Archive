---
title: "Can't Read ext3 on XP"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by zepl on 2009-12-04
I had been using fs-driver.
Reinstalled xp then ubuntu 9.10
Didn't work anymore, something about a mount problem.
No idea.

---

### Post by halitech on 2009-12-04
did you reinstall the fs-driver?

---

### Post by zepl on 2009-12-04
Of course, looked around on the site. 
Don't know how to use the mountdiag tho.
[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)
can't findnice instructions or I'm just dumb I guess

---

### Post by halitech on 2009-12-04
[http://www.fs-driver.org/faq.html#conf_drv_ltr](http://www.fs-driver.org/faq.html#conf_drv_ltr)

---

### Post by louieb on 2009-12-04
Usually its the inode size - ex2ifs works only if inode size is 128.

to check ( remember to change @# to point to the ext3 partition yout trying to access)
```
sudo tune2fs -l /dev/sd[COLOR=Red]@#[/COLOR] | grep -i inode

```

---

