---
title: "Uuid"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-06
how do you get the UUID for a partition or drive?

---

### Post by sdennie on 2009-01-06
Try:

```

blkid

```

Or:

```

ls -l /dev/disk/by-uuid

```

---

### Post by tech9 on 2009-01-06
> **theozzlives said:**
> how do you get the UUID for a partition or drive?

to change your uuid....

```
sudo gedit /etc/fstab
```

be careful when editing fstab

T9

---

### Post by ajgreeny on 2009-01-06
I seem to always need **sudo** for the **blkid** command, though I have seen others who say it's not necessary.

---

### Post by theinnercityhippy on 2009-01-06
> **tech9 said:**
> to change your uuid....

```
sudo gedit /etc/fstab
```

be careful when editing fstab

T9

Erm, this is a really really bad for someone new to linux. You could very easily cause your computer to stop loading at all by changing anyhting in this file.

Unless you really know what you are doing here, it is best left well alone.
(You ought to know better tech9 ;) )

-JimDog*-

---

### Post by sisco311 on 2009-01-06
some useful links:
[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by theozzlives on 2009-01-07
> **theinnercityhippy said:**
> Erm, this is a really really bad for someone new to linux. You could very easily cause your computer to stop loading at all by changing anyhting in this file.

Unless you really know what you are doing here, it is best left well alone.
(You ought to know better tech9 ;) )

-JimDog*-

I've edited the fstab before, matter of fact I posted this:
[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")
I just need to know the UUID of Home when I resize it.

---

