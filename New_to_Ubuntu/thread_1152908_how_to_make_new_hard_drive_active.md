---
title: "how to make new hard drive active"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by icivilion on 2009-05-08
hi all... i have purchased a new hard drive ... i formatted it using gparted in ext3... but i am not able to copy any thing into my external hard drive.... hard drive get mounted and there only one folder inside by lost+found... how to activate my partion...?????? i know this is very easy task for you guys... thanks in advance...

---

### Post by Kareeser on 2009-05-08
The drive is already initialized and running. You may not have permissions to write to the drive, however.

Check it for me?

```
cd /media
ls -l
```

---

### Post by icivilion on 2009-05-08
hi this was the output......i am total numb:)

indu@Kina:~$ cd /media
indu@Kina:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2009-05-06 14:33 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-05-06 14:33 cdrom0
drwxr-xr-x 3 root root 4096 2009-05-09 16:21 ext3 indu



NEXT WHAT TO DO... PLEASE HELP....

---

