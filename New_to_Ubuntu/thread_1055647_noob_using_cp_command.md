---
title: "noob using cp command"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by warrior24 on 2009-01-30
adrian@adrian-desktop:~$ cp -r /home/adrian/Desktop/Backup /media/disk
cp: cannot create regular file `/media/disk/Backup/xorg.conf ': Invalid argument
adrian@adrian-desktop:~$ 


what am I doing wrong trying to copy folder with file in it and i get this error.

---

### Post by handydan918 on 2009-01-30
> **warrior24 said:**
> adrian@adrian-desktop:~$ cp -r /home/adrian/Desktop/Backup /media/disk
cp: cannot create regular file `/media/disk/Backup/xorg.conf ': Invalid argument
adrian@adrian-desktop:~$ 


what am I doing wrong trying to copy folder with file in it and i get this error.

Just a thought...
Try a trailing slash after /Backup

So the new command would be..```
.cp -r /home/adrian/Desktop/Backup/ /media/disk
```

---

### Post by warrior24 on 2009-01-30
yeah the slash after it worked thanks , I also got it to work with 
cp -r  /home/adrian/Desktop/backup /media/disk         


   thanks handydan

---

