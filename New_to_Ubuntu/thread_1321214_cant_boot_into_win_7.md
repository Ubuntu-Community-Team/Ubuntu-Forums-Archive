---
title: "cant boot into win 7"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by daveedking on 2009-11-09
hey ubuntu.i was duel booting 9.10 and win7.deleted the ubuntu partiton and joined eveeything back into win7 partition.
wooopps. i reboot and i get error:no such partition
grub rescue>
could some1help

---

### Post by ranch hand on 2009-11-09
You just need to retore your Win JerryLewis Pro boot sector.  Boot your install disc.  It should be an option.

---

### Post by daveedking on 2009-11-10
> **ranch hand said:**
> You just need to retore your Win JerryLewis Pro boot sector.  Boot your install disc.  It should be an option.

hey thank you for the help.
i** solved** my problem..
1.boot from windows 7 retail dvd.
2.run repair computer.
3.command prompt enter(bootrec/fixmbr) (bootrec/fixboot)

[B]hope this helps someone like it helped me.

[/B]

---

