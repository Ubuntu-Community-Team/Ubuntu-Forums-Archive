---
title: "grub editing, fs mount changes"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by bigO on 2008-12-31
I'm assuming the absolute beginner talk thread is the correct place for this question.

I have recently tried to dual boot ubuntu and ubuntu studio which went well enough I suppose but I now wish to get rid of the studio partition from the grub menu and re-integrate the 70 GB partition into my regular ubuntu set-up so I don't have to mount it myself every time. could someone kindly direct me to the proper tut or something please? I tried a google search but I guess I'm not using the proper key words b/c i just get general partitioning links.

Any help would be greatly appreciated.
Thank you in advance.

---

### Post by Tim Sharitt on 2008-12-31
If you just want to mount the partition at boot time add it to fstab
```
gksu gedit /etc/fstab
```
then add
```
/dev/sdxx   /mountpoint    ext3   auto,users,rw,relatime  0      0
```
substituting sdxx with the partition your mounting and mount point with where you want the partition mounted. 
See this thread for more information: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bigO on 2008-12-31
Thank you Tim I appreciate the help.

---

