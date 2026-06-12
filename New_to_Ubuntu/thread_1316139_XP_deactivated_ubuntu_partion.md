---
title: "XP deactivated ubuntu partion?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by seth_reaver on 2009-11-05
I installed ubuntu 9.10 and when i installed xp after it, it said it would deactivate it. How do i Reactivate it?

---

### Post by kansasnoob on 2009-11-05
If your Ubuntu 9.10 was a fresh install it probably had grub2 so this would be the basic idea:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

If you need more detailed help then boot the Live CD choosing "try Ubuntu without changes to disc" and go to terminal and post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by Mark Phelps on 2009-11-06
Nevermind ... misread the post.

---

