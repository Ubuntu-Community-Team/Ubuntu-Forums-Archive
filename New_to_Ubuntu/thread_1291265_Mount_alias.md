---
title: "Mount alias"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-10-14
From time to time to I mount two different filesystems, let call them StorageA (sda1) & StorageB (sda2), but I don't wish them to be automounted nor that no password is required. Therefor I thinking about creating a alias for this purpose but I'm, unsure how, most guides tell me to mount filesystems in /mnt while gnome mount them in /media, why? When gnome mount the disks show up as a icon on the Desktop while if I do it manually they don't, can this be fixed?

 ```

sudo mount /dev/sda1 /media/StorageA &&
sudo mount /dev/sda2 /media/StorageB

```

---

### Post by Baelus on 2009-10-14
/mnt and /media are both used to mount partitions, but ubuntu uses /mnt for local, fixed hard drives while /media is used for removable media like sd cards, mp3 players, etc.

When /media is used gnome adds an icon to the desktop. Partitions in /mnt will not have any icons displayed.

AFAIK, that's the only real difference between the two. It's more cosmetic than anything else.

I'm not sure what you want to do with an alias or passwords when automounting filesystems. Give some more details and I'll see if I can help.

---

### Post by SpinningAround on 2009-10-14
Thanks for the answer the questions I did have

---

### Post by SuperSonic4 on 2009-10-14
That should work without a problem - so long as the partition path doesn't change

---

