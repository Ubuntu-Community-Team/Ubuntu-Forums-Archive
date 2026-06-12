---
title: "Doesn't go to Trash, gets delete directly"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by | Gnome | on 2009-10-10
I use a NTFS partitioned drive to store data in Ubuntu. When I delete files from that drive it gets delete directly, it doesn't go to Trash. So, if I mistakenly delete something, then it's gone. However, things deleted from Ubuntu (root and desktop) go to Trash. What can be the solution?? Please help!!

---

### Post by Dangger on 2009-10-10
> **| Gnome | said:**
> I use a NTFS partitioned drive to store data in Ubuntu. When I delete files from that drive it gets delete directly, it doesn't go to Trash. So, if I mistakenly delete something, then it's gone. However, things deleted from Ubuntu (root and desktop) go to Trash. What can be the solution?? Please help!!

I had exactly the same problem and it's been solved. [Here]("http://ubuntuforums.org/showthread.php?t=1228323") are the steps you need to follow, it's quite easy really.

The issue has to do with ownership of the partition.

---

### Post by | Gnome | on 2009-10-10
When I entered the code

*sudo mount /dev/sdXX -t ntfs /media/Documents -o uid=1000* 

as

*sudo mount /dev/sd**a5** -t ntfs /media/**Possessions** -o uid=1000*

following error was shown- **fuse: mount failed: Device or resource busy**

What's the problem??

---

### Post by Dangger on 2009-10-10
> **| Gnome | said:**
> When I entered the code

*sudo mount /dev/sdXX -t ntfs /media/Documents -o uid=1000* 

as

*sudo mount /dev/sd**a5** -t ntfs /media/**Possessions** -o uid=1000*

following error was shown- **fuse: mount failed: Device or resource busy**

What's the problem??

I'm guessing it's already mounted since you can access the files and delete them. Try unmounting it and see if it works and then mount it again. If it works that way then you only need to modify fstab accordingly:

```
gksudo gedit /etc/fstab
```

and add the corresponding line for your device to create a mounting point. After that, restart the system and it should be properly mounted and then you will be able to delete files and send them to the wastebasket.

---

