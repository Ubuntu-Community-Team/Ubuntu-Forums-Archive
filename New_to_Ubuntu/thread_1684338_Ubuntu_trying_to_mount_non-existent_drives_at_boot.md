---
title: "Ubuntu trying to mount non-existent drives at boot"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-02-09
I got my hard drive copied and the old one pulled today (many thanks to Rhizoid) but now I have two partitions on my 'Places' menu that no longer exist and Ubuntu tries to mount them at boot. I booted with the live cd and took a look at the current partitions with gparted - everything looks fine there. I can't remove them from my places list. when I try to click on them I get 

```
mount:special device sdb2 does not exist
```

Before I started all this I did make a backup copy of fstab, will replacing the current fstab with it cure this?

thanks

mystmaiden

---

### Post by taseedorf on 2011-02-09
try looking into /etc/fstab 

sudo gedit /etc/fstab

and remove the non-existent drives

---

### Post by mystmaiden on 2011-02-09
Thanks so much, that fixed it!

---

