---
title: "permission error with new partition"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-18
note when i try to copy a file to this partition i get this error

There was an error copying the file into /media/93bb2ea0-db9a-42a4-aa06-f47c4d9cb20c.

Error opening file '/media/93bb2ea0-db9a-42a4-aa06-f47c4d9cb20c/ubuntupocketguide-v1-1.pdf': Permission denied

just created this partition so how do i correct/tks

---

### Post by rburkartjo on 2010-07-18
just need to be able to access it and add whatever

---

### Post by rburkartjo on 2010-07-18
note root is the owner of this partition so i cant access it how can i change to ray or at least share access with/tks

---

### Post by rburkartjo on 2010-07-18
found this solution note the reply by scouser73

[http://ubuntuforums.org/showthread.php?t=1423255](http://ubuntuforums.org/showthread.php?t=1423255)

---

### Post by aidenscool09 on 2010-07-18
Have you tried going to the partition in a file manager as Root? Open up a Terminal and do 
```
sudo nautilus
```
Then go to the partition and right click the space. Then go over to permissions and change everything to "Read & Write". It should work, if not, i'll think of something else. In the meantime, Google is your friend.

     Aidenscool09

---

### Post by da burger on 2010-07-18
> **aidenscool09 said:**
> ```
sudo nautilus
```

That should be ```
gksudo nautilus
```
It's always best to use gksudo rather than regular sudo for GUI programs.

---

### Post by aidenscool09 on 2010-07-18
Oh well, im just used to sudo for everything, if not i use "sudo su". And whats the difference?

---

### Post by rburkartjo on 2010-07-18
da tks i just forgot to post my link on my response

---

### Post by aidenscool09 on 2010-07-18
Ok, thats fine. And before you think i'm a newbie because of my low post count, it's just i never used Ubuntu Forums before other than reading replies and i'm actually petty good with Linux in general. And remember to mark this post as [SOLVED].

---

### Post by da burger on 2010-07-18
> **aidenscool09 said:**
> Oh well, im just used to sudo for everything, if not i use "sudo su". And whats the difference?

This article sums it up nicely I think. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by PPPilot on 2010-07-18
Sounds like a basic problem with permissions.

Use chown and chmod to set permissions.

```
sudo chown user.user /media/mount_point
sudo chmod 770 /media/mount_point
```See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by aidenscool09 on 2010-07-18
Yeah cheers mate.

---

