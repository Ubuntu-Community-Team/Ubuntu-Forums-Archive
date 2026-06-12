---
title: "How to search a specific drive"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by WA3ERQ Jim on 2010-10-10
Here is my issue.  I'm using Ubuntu 10.04 and I'm still learning Linux.  I do have a knowledge of DOS commands.  My laptop has two drives and one is showing a fault at startup (before Linux starts).  I want to list the files on a specific drive and attempt an FDISK and Format of that drive but can't seem to figure out how to list the files on a specific drive.  I've tried "ls" with no luck.

Thanks
Jim
WA3ERQ

---

### Post by jtarin on 2010-10-10
Is the drive mounted? When you "cd" to the directory and run "ls" what is returned in the terminal?

---

### Post by WA3ERQ Jim on 2010-10-10
That's what I can't seem to figure out how to do.  I tried cd sda1    cd /sda1  cd /dev/sda1 and the response is :bash: cd: sda1: No such file or directory

---

### Post by nothingspecial on 2010-10-10
```
sudo fdisk -l
```

```
mount
```

Don`t try to cd into /dev/blah

cd into the mount point

---

### Post by mikewhatever on 2010-10-10
Have you tried 'ls -laR'? There is no way all of the output is going to fit on the screen, so you might want to redirect it into a file.

ls -laR > filelist.txt

Obviously, the command must be pointed to the mount point(/, /home, /media), not the device name (dev/sda1).

---

