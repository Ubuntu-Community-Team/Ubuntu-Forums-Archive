---
title: "how to access other hard disk partition."
date: 2010-10-30
forum: New to Ubuntu
---

### Post by gauravgupta on 2010-10-30
i have dual booted ubuntu with win7..
now i want to access other hard disk partitions from the terminal.
i am unable to access through media dir. its says no file or dir exist whereas when i view subdir using ls cmd it show my partitions.
please tell how to access those partitions.

---

### Post by bioterror on 2010-10-30
> **gauravgupta said:**
> i have dual booted ubuntu with win7..
now i want to access other hard disk partitions from the terminal.
i am unable to access through media dir. its says no file or dir exist whereas when i view subdir using ls cmd it show my partitions.
please tell how to access those partitions.

Im pretty sure that your windows lies in /dev/sda1

So the magic words are:
```

cd /media
sudo mkdir Windows
sudo mount.ntfs-3g /dev/sda1 /media/Windows

```

---

### Post by gauravgupta on 2010-10-30
> **bioterror said:**
> Im pretty sure that your windows lies in /dev/sda1

So the magic words are:
```

cd /media
sudo mkdir Windows
sudo mount.ntfs-3g /dev/sda1 /media/Windows

```
thnx for your reply, but it is not sda1
also it has 2 more logical partition..
how to check all partitions?
and How to unmount it..

---

### Post by Verbeck on 2010-10-30
> **gauravgupta said:**
> thnx for your reply, but it is not sda1
also it has 2 more logical partition..
how to check all partitions?
and How to unmount it..

you can check all partitions by running 
[B]sudo blkid -c /dev/null
[/B] 
to unmount
**sudo umount /dev/devicename  **or[B]
sudo umount /mount/point
[/B]

---

### Post by gauravgupta on 2010-10-30
> **Verbeck said:**
> you can check all partitions by running 
[B]sudo blkid -c /dev/null
[/B] 
to unmount
**sudo umount /dev/devicename  **or[B]
sudo umount /mount/point
[/B]
thanx for ur reply

---

### Post by gauravgupta on 2010-11-01
> **Verbeck said:**
> you can check all partitions by running 
[B]sudo blkid -c /dev/null
[/B] 
to unmount
**sudo umount /dev/devicename  **or[B]
sudo umount /mount/point
[/B]
i stiil have problem..view the image below..
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=174163&stc=1&d=1288595519[/IMG]

please help..its urgent

---

### Post by Verbeck on 2010-11-01
alright, try this
[B]
cd /media
sudo mkdir Drive1 Drive2
sudo mount /dev/sda2 /mount/Drive1
[/B]**sudo mount /dev/sda3 /mount/****Drive2**

EDIT : before trying that, go to System>Administration>Disk utility and try to mount the drive from there

---

