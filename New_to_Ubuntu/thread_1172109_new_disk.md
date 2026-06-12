---
title: "new disk"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by dimitriv on 2009-05-28
hi

i just added a new second hdd. i chose the default partition table MSDOS then created 2 EXT3 partitions. After reboot the new partitions are visible but I do not have permissions to create files or folders. How do i set these permissions so i own these partitions.

Thank you

---

### Post by glotz on 2009-05-28
Change the ownership of the disks to you.```
sudo chown -R username:usergroup /path/to/mounted/disk/
```
By default your usergroup is the same as your username.

---

### Post by pmj85 on 2009-05-28
I was about to post something about the 'root' account which I read about; I thought you'd have to log in as that and change the permissions from there.

That said I've been using Ubuntu for 2 days and know absolutely nothing about it. Good job glotz was on hand :-k

Good luck with it!

---

### Post by dimitriv on 2009-05-28
glotz

it worked a treat - thank you

---

### Post by glotz on 2009-05-28
Glad to be of use.

Welcome to the tribe guys! :)

---

### Post by pmj85 on 2009-05-28
Cheers, glad to be here :D

I'd be a liar if I said I wasn't as confused as hell, though. Lots to learn! :)

---

### Post by glotz on 2009-05-28
And even more to unlearn! ;)

---

### Post by NHArticleTen on 2009-05-28
> **glotz said:**
> And even more to unlearn! ;)

isn't that the truth

---

