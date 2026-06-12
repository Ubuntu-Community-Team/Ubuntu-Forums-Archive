---
title: "Problem with full accessing of a pen drive"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2009-07-21
Hello friends. I have recently installed ubuntu and i am having problem deleting files on my pen drive, though there is absolutely no problem in reading contents  on the pen dive but when i try to modify the files or try to delete it, it shows files access set to read-only... Can anyone help me to solve this problem??

---

### Post by Grenage on 2009-07-21
Hello there,

Assuming that the drive isn't locked (if it even has a lock):  Are you able to write to the drive as root?  Let's say that the drive auto-mounts and pops up on the screen when you insert it, note the location in the address bar; it will likely be /media/something.  Open a command prompt and type "gksu nautilus", enter the password when requested and then type the address from earlier into the address bar.

You could do the same test from a terminal a lot quicker, but since you've just installed ubuntu, I'm taking the most user-friendly path.

---

### Post by viditgoyal3009 on 2009-07-21
I am not being able to write anything on pendrive and "gksu nautilus" was unable to help me... Is there any other way to rectify this????

---

### Post by Astarroth on 2009-07-21
Not sure if this will help or not. I had a problem with a thumb drive not letting me write to it and fixed it by formating the stick under ubuntu. Of course you will want to get anything off of the drive that you want to save first. Just format the stick back to fat32 if you are going to be sharing it with any windows devices. My drive is working with no problems now, can access and read or write to it in linux and windows.

---

### Post by swerdna on 2009-07-21
Can you open the Gnome terminal (application --> accessories ->- terminal) and enter this command and copy/paste the whole dialogue back here: ```
df -Th
``` 
That should reveal the mounted partitions/drives and their mount points/paths. Suppose the pen drive is mounted at /path_to/mount_directory. Enter this command in the terminal and post those results back here too:```
ls -l /path_to/mount_directory
```

From these data we should be able to see the files in the drive and the permissions on the files and the filesystem of the drive -- and advise you what to do.

---

