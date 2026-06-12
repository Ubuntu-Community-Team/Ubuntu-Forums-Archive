---
title: "Can not move files to partitions"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by PPPilot on 2009-12-14
I am running Karmic and have created partitions on my 3 drives. Of course the Karmic partition is ext4. At first I created an ext4 partition on another drive and it would mount but I could not save files getting this error: error opening '/media/storage/elliot2.xls': Permission Denied. I repartitioned it to ext3 and it worked. I then formated other partiions to ext3 but they then gave me this same error when I tried to copy a file there. I repartitioned to the various Windows formats FAT32, NTFS etc. and they all worked fine.
All partitioning has been done using Gparted. I have openSUSE 11.2 installed on another partition and it will allow me to mount these partitions but it will not allow me to copy files there either. So my question is since I have to enter my password to mount these partitions, why do I not have permission to save to them????

---

### Post by bodhi.zazen on 2009-12-14
Sounds like a basic problem with permissions.

Use chown and chmod to set permissions.

sudo chown user.user /media/mount_point
sudo chmod 770 /media/mount_point

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by PPPilot on 2009-12-14
Thanks a lot, That solved the problem.

---

### Post by bodhi.zazen on 2009-12-14
> **PPPilot said:**
> Thanks a lot, That solved the problem.

Sweet, I see you are a fast learner =)

---

