---
title: "I have somehow filled my root partition and can't figure out how..."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by shortridge11 on 2010-04-30
I was moving stuff around my home file server (9.10) and i think i tried moving stuff to something that wasn't mounted right. Either way, now my root drive is full and i can't figure out what happened.  I used the disk analyzer to try to figure out where it went, but no luck there. Here is the output of df

```

xx@xxx:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              74G   70G     0 100% /
udev                 1006M  296K 1006M   1% /dev
none                 1006M     0 1006M   0% /dev/shm
none                 1006M  492K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sdb6             112G   76G   36G  69% /media/m1
/dev/sdb7             1.2T  829G  381G  69% /media/g1
/dev/sde1             1.4T  1.4T  1.4G 100% /media/m2
/dev/sda3             323G  4.2M  323G   1% /media/m3
/dev/sdd1             1.4T  1.2T  261G  82% /media/t1
/dev/sdc1             1.4T  1.1T  311G  78% /media/t2
/dev/sda2             293G  4.2M  293G   1% /media/t3
/dev/sda1             782G  294G  488G  38% /media/c1

```

Although when i use the disk analyzer it said t3 and m3 had only 6 bytes available. Any ideas?

---

### Post by 4Orbs on 2010-04-30
Same thing happened last year to me. I'm not sure how to word this, but this is what happened. I forgot to mount my extra media partition, but then copied a bunch of video files to that folder... since the partition wasn't mounted, those videos were copied to the folder but they went into the root partition because the media partition wasn't mounted. So, in essence, I had those files duplicated... one in the media partition and one in the root partition (the folder was the same name in both partitions).

To find out if this is what happened to you, first unmount the partition in question... then, when you are sure that it is unmounted, go take a look at the media FOLDER and see if the files are still showing up. If they do show up, you can delete them (which will remove them from the root partition, but won't remove them from the media partition because it is not mounted).

---

### Post by shortridge11 on 2010-04-30
that seems to be exactly what i did. thanks! =D

---

### Post by 4Orbs on 2010-04-30
A word of caution: When you delete those files from the media folder you need to be root user. Also, deleting those files will move them into the root trash bin, so the root partition will still be full until you empty the root user's trash. The problem (if it still exists nowadays) is that when you're using Nautilus and try to empty the root trash bin... you won't be able to open the root trash bin (you'll get a permission denied error). There is a way to empty the root trash, but I don't remember what that method entails (I haven't used Nautilus for a long time now).

EDIT: And be sure the media PARTITION is not mounted when you remove the files from the media FOLDER.

---

### Post by KinKiac on 2010-04-30
> **4Orbs said:**
> A word of caution: When you delete those files from the media folder you need to be root user. Also, deleting those files will move them into the root trash bin, so the root partition will still be full until you empty the root user's trash. The problem (if it still exists nowadays) is that when you're using Nautilus and try to empty the root trash bin... you won't be able to open the root trash bin (you'll get a permission denied error). There is a way to empty the root trash, but I don't remember what that method entails (I haven't used Nautilus for a long time now).

Just open a terminal and type **sudo nautilus** and enter your pass.  You'll now have nautilus open with root permissions, however BE CAREFUL, delete the wrong thing and you're screwed.

---

