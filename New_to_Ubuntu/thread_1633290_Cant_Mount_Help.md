---
title: "Cant Mount Help"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-11-29
I was messing around and did something. Now i cannot mount my data partition. I used to be able to click on the partition and it would mount in 2 to 3 seconds.  Now when i do that it tells me i need root privileges.  How do i go back to the way things used to be?

---

### Post by hunter99507 on 2010-11-29
This is the error i get

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb5 on /media/sdb5

---

### Post by Verbeck on 2010-11-29
try from a terminal 
```
sudo mount -a
```also, if the drive is set in fstab, it'll mount at login

---

### Post by hunter99507 on 2010-11-29
That didnt work. I can still mount my windows partition no problem, but not this data partition.

---

### Post by hunter99507 on 2010-11-29
I fixed it. I had additional entrys in fstab, so i deleted them and now its fixed.

---

### Post by amjjawad on 2010-11-29
I know you fixed it but [this]("http://ubuntuforums.org/showthread.php?t=872197") might be helpful in the future ;)

---

### Post by hunter99507 on 2010-11-30
> **amjjawad said:**
> I know you fixed it but [this]("http://ubuntuforums.org/showthread.php?t=872197") might be helpful in the future ;)

Thanks amjjawad, this is easy. I wish i started with this.

---

### Post by amjjawad on 2010-11-30
> **hunter99507 said:**
> Thanks amjjawad, this is easy. I wish i started with this.

You welcome mate and as they say: Never too late :)

---

