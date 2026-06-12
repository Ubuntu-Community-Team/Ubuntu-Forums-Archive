---
title: "messed up partition"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by shahmish on 2011-04-11
I ran mkfs in the terminal to format a partition. Ended up with 130 gigs of memory that i cannot use unless I am root. 

I can't read, create or edit the files on it, unless I am logged in as root and do that through the terminal.

 I tried to fix it with gparted, but that had the same result. 

I assume the reason is that I did not specify the permissions when I ran mkfs, and that put the permission set to default, and since I ran the command as root, well, now I have to be root to operate the partition. 

Anyway, my question is, how can I fix this?
Thanks.

---

### Post by shahmish on 2011-04-11
If ti helps, in the terminal I used ext2, in Gparted ext4...

---

### Post by TeoBigusGeekus on 2011-04-11
Change the owner of the partition's mount point
```
sudo chown -R yourusername /media/your_hd_mount_point
```

---

