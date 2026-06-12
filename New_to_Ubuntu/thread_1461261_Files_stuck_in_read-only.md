---
title: "Files stuck in read-only"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by I8NY on 2010-04-24
Okay this has to be a stupid question, how do i delete or change files that are set to read-only.  I used a app called video4fuze and all the files it makes are read only and i can't delete them.  I tried change the read-only to read & write but has a error telling it is read only.:(  I even tried deleting them with nautilus as root and that didn't work.  What am i doing wrong?

---

### Post by UltraMathMan on 2010-04-24
```
sudo chmod +w /path/to/file/
``` This will make the file writable.

---

### Post by I8NY on 2010-04-24
okay and how do i get spaces " " in the path to the file.  And is there a way to do a whole folder of files?

---

### Post by UltraMathMan on 2010-04-24
Sure, just enclose paths with spaces in quotes, and add the -R (recursive) option: ```
sudo chmod -R +w "/path to/file"
```

---

### Post by I8NY on 2010-04-24
okay that got it to run but it still doesn't change the permissions. Yes with sudo command.
```
chmod: changing permissions of `/media/SANSA FUZE/VIDEO/xxxx.AVI': Read-only file system

```

---

### Post by UltraMathMan on 2010-04-24
Ahhh, it's not the files that are read only, it's the filesystem. The Sansa Fuze is being mounted as read-only, so naturally, you can't write or modify files on it. Try the following ```
sudo umount "/media/SANSA FUZE/"
``` then try remounting it manually with ```
sudo mount "/media/SANSA FUZE/"
``` That should mount it in read/write mode.

---

### Post by I8NY on 2010-04-24
yea it worked!  thanks for you help, Ubuntu must have mounted it wrong or something thanks again.

---

### Post by UltraMathMan on 2010-04-24
No problem, glad I was able to help!

---

### Post by Nizzok on 2010-05-19
Hi,  I've run into the same problem but this doesn't seem to be working. I'm running Lynx on a lenovo g450, and I can't my external drive from mounting as read-only. I've followed the directions here. any suggestions?

---

