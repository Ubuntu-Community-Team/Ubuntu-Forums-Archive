---
title: "Mount Windows Drives"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by sharks on 2009-02-16
I have a problem now...I have already mounted my windows drives but the problem is that now the last time i used window$ i installed a anti virus software and now i can boot windows well and it hangs when the AV loads.....And i switched it off manually...Now the problem is that i need windows drives to boot as i have some important files in it....if i try to mount windows drives,it say "you are not priviligd to mount the volume....  -----" Can you guys help me?

---

### Post by Tim Sharitt on 2009-02-17
Are you trying to mount it in nautilus?

What do you get from the command line with
```
sudo mount -t ntfs-3g /dev/sdxy /mountpoint
```
substituting sdxy with your windows partition and mountpoint with the directory you want the drive mounted at.

---

