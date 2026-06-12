---
title: "How do you automatically mount a partitioned &quot;filesystem&quot;"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by meteora184 on 2010-05-28
I recently partitioned my window PC and put ubuntu in it.  I can access the windows partition easily by double clicking on it, however I know there is a way to make it so it automatically mounts. (it would help because my Rythmbox library is in the other harddrive, and I forget to mount it sometimes)

I know there is a way, but I cannot figure it out.
Thanks alot in advance.

---

### Post by bumanie on 2010-05-28
In terminal > sudo apt-get install ntfs-config then go to Applications --> System tools --> Ntfs configuration tool. Click on that, fill out the gui and the windows drive will be added to /etc/fstab and be mounted at boot.

---

### Post by Tahakki on 2010-05-28
There's an easier way...add this to your /etc/fstab:

```
/dev/sda1 /mnt/sda1 ntfs users,defaults,umask=000 0 0
```

Replacing /dev/sda1 with where the drive is and /mnt/sda1 with, say, /media/Windows. Up to you.

---

