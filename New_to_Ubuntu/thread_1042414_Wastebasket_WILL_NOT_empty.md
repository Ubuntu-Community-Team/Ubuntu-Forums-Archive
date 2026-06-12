---
title: "Wastebasket WILL NOT empty"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by jecarr33 on 2009-01-17
I kinow there has to be a super sweet way to get rid of the these things in the waste basket.  I've hit empty trash about a million times.  Someone PLEASE HELP!!!


Thanks in advance!!

-Jonathan

---

### Post by jerome1232 on 2009-01-17
there is, I'm guessing that you somehow got a file owned by root in there.

This will recursively force the deletion of all files in your user's trash.
```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by jecarr33 on 2009-01-17
Yeah that worked....the items are no longer in the trash but AWM is still showing there are 3 items present.  I'm assuming I'll need to reboot to get that to change?  Thanks again!! 

-Jonathan

---

### Post by jeff betts on 2009-09-03
Thanks jerome1232 that worked.

---

