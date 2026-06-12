---
title: "remastersys/disk usage"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by dzon65 on 2010-07-15
Hi.Did a backup with remastersys,burned the iso and deleted the remastersys contents in home afterwards (sudo remastersys clean).However,the remastersys folder is still in the home directory (empty though) and there's still some aditional disk space being used.Around 4.5 Gb,the amount there was being used before the backup.Anyone some ideas?
Regards,J.

---

### Post by gr4nf on 2010-07-15
I believe remastersys clean only gets rid of temporary files used during the process. You say 4.5 gigs of space are still being used? It sounds like that .iso file you made is still there somewhere in your system. If you no longer want it, as it is now on the cd, just find it and delete it.

As for the remastersys directory in home, it is supposed to stay. Clean won't delete it. If you want to delete it, drag it to the trash or run:
```

rm -rf /home/"name of directory"

```

---

### Post by dzon65 on 2010-07-15
Well,I've looked it up,no remastersys related file that size can be found.The iso itself took some 2.4 Gb,it's as if the system's size (4.5 Gb) has  been duplicated. Gonna try that command.

---

### Post by dzon65 on 2010-07-15
Could it be the discanalizer's acting weird?

---

### Post by dzon65 on 2010-07-15
Must be missing something.

---

