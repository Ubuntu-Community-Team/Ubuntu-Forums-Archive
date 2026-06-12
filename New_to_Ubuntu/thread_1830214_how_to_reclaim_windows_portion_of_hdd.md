---
title: "how to reclaim windows portion of hdd"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by DarinB on 2011-08-21
I recently bought a Dell inspiron 560 it runs great. it was so inexpensive i am thinking of getting a second one. to have a windows box and a separate Ubuntu work machine. Is there any way to reclaim the windows portion of the the Hdd I have on this machine? with out doing a full wipe out and reinstall. I could use the Hdd space on this machine? 
can I wipe out the windows portion and add it to the existing ubuntu partition? or better to start over?

---

### Post by sanderd17 on 2011-08-21
Yep, just boot up with a live CD, start gparted, delete the windows partition(s), enlarge the Ubuntu partition(s) as needed, reboot and execute

```

sudo update-grub

```
to remove the windows entry from your grub menu.

---

### Post by Mark Phelps on 2011-08-21
> **DarinB said:**
> ...Is there any way to reclaim the windows portion of the the Hdd I have on this machine? with out doing a full wipe out and reinstall. I could use the Hdd space on this machine? 
can I wipe out the windows portion and add it to the existing ubuntu partition? or better to start over?

Depends .. do you know for sure that Ubuntu has its own partitions? That you did NOT install using Wubi?

IF so, then to expand the partition that Ubuntu uses, since you can't do this while Ubuntu is running, you will have to boot from the Ubuntu CD.

Then, run Gnome Partition Editor (GParted), select the partition you want to expand -- confirming that it is NOT mounted, and resize it.  Be prepared to WAIT.  Gparted is S...L...O...W -- since it does two complete passes, and interrupting it will corrupt your filesystem.

---

