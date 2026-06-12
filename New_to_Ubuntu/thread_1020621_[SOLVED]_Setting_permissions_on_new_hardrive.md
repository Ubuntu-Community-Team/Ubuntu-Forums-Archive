---
title: "[SOLVED] Setting permissions on new hardrive"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by mkvnmtr on 2008-12-24
I have an external hardrive that I have been using on my Mac and on my Ubuntu butn it ws set up on the Mac for backup. I decided that I don't need to back up the Mac since I use Ubuntu all the time. I copied all the stuff I wanted and deleted the three partitions and made a new disklabel on GParted. Then I made a new partition. When I try to use it I can't. It says it can't determine the permissions. When I try to use chmod to set permissions I can't seem to get it to work. Can somebody tell me how to set permissions for the first time on this disk. I have benn searching the forum and also Google and still con't seem to get it to work.

---

### Post by taurus on 2008-12-24
What filesystem is it?

```
sudo fdisk -l
```

---

### Post by mkvnmtr on 2008-12-24
I set it to est 2 in GParted.

thats ext 2. I am the worlds worst typer.

---

### Post by taurus on 2008-12-24
I will assume it is /dev/sdb1 and your login name is bill, you could so something like

```
sudo mkdir /media/sdb1
sudo mount -t ext2 /dev/sdb1 /media/sdb1
sudo chown -R bill:bill /media/sdb1
ls -la /media
```
And when you are done, don't just unplug it from your computer.  You need to unmount it first.

```
sudo umount /media/sdb1
```

---

### Post by mkvnmtr on 2008-12-24
Thank you I can now use the drive but it still says the permissions can not be determined. Maybe it will take a log out or something. At least I can use it.

---

### Post by taurus on 2008-12-24
What are the outputs of these commands?

```
sudo fdisk -l
df -h
ls -la /media
id
```

---

### Post by mkvnmtr on 2008-12-24
Here are the results of those commands

---

