---
title: "Is there a way to force a fsck on all drives upon next reboot?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by diablo75 on 2009-05-22
FSCK corrected an error in my root partition today and I'd like to force a check on all other partitions to ensure they don't house any errors as well.  How can I go about doing this?

---

### Post by sisco311 on 2009-05-22
[s]```
sudo shutdown -Fr now
```[/s]
Or create an empty file called forcefsck in the root of the partition:

```
sudo > /forcefsck
sudo > /media/partition/forcefsck
sudo > /home/forcefsck

```

and reboot

---

### Post by juancarlospaco on 2009-05-22
Theres a GUI too!, but i dont remember the name :(

---

### Post by sisco311 on 2009-05-22
> **juancarlospaco said:**
> Theres a GUI too!, but i dont remember the name :(

Yes, gparted can check partitions.

@diablo75

you can unmount the partition and run the check manually.

for an ext2/ext3 partition the command is:
```
sudo umount /dev/sdXY
sudo e2fsck -C0 -p -f -v /dev/sdXY
```

---

### Post by lovinglinux on 2009-05-22
[http://ubuntuforums.org/showpost.php?p=3809681&postcount=2](http://ubuntuforums.org/showpost.php?p=3809681&postcount=2)

---

### Post by Hospadar on 2009-05-22
the "e2fsck" command controls how often drives get fsck'd on bootup, you could set it to every bootup if you wanted, or just set the counter to whatever to make it check on your next bootup.  If you just want to check it though, you can just run fsck yourself (obviously)  You may also want to consider checking from a livecd as some very major problems (if you think you have some major problems, or if fsck reports them) can only be fixed when the filesystem is offline.  also ext2/3 (not sure about 4) can only be defragged offline (i.e. via livecd)

---

### Post by HeirPixel on 2009-05-22
> **sisco311 said:**
> ```
sudo shutdown -Fr now
```
The **-F** tag has been deprecated since 6.10 (Edgy). [https://launchpad.net/ubuntu/+source/upstart/+bug/74139]("https://launchpad.net/ubuntu/+source/upstart/+bug/74139") has a little background.

---

### Post by sisco311 on 2009-05-22
> **HeirPixel said:**
> The **-F** tag has been deprecated since 6.10 (Edgy). [https://launchpad.net/ubuntu/+source/upstart/+bug/74139]("https://launchpad.net/ubuntu/+source/upstart/+bug/74139") has a little background.

Yep, you're right. ](*,)

> **Hospadar said:**
> the "**tune2fs**" command controls how often drives get fsck'd on bootup 
<snip>

;)

```
tune2fs -C 30 /dev/sdXY
```

---

### Post by Bladeforger on 2009-05-28
```
tune2fs -C 30 /dev/sdXY
```[/QUOTE]

I looked at the man pages for tune2fs, and I don't understand 2 things:

1. How does the above command know that we are changing the mount-count and not the max-mount counts?

2. What is the purpose of the /dev/sdXY part of the command?

Thanks!!:popcorn:

---

### Post by binbash on 2009-05-28
sudo touch /forcefsck

then reboot

---

### Post by sisco311 on 2009-05-28
> **Bladeforger said:**
> ```
tune2fs -C 30 /dev/sdXY
```

I looked at the man pages for tune2fs, and I don't understand 2 things:

1. How does the above command know that we are changing the mount-count and not the max-mount counts?


Linux is case sensitive. You can change the max-mount-count with the -c (lowercase C) option and the mount-count with the -C (uppercase C) option.

> 
2. What is the purpose of the /dev/sdXY part of the command?

Thanks!!:popcorn:

/dev/sdXY is the name of the partition. You can list the partitions with:
```
sudo fdisk -l
```
You can also list your mounted devices and their descriptions with:
```
mount
```

/dev/sda1 is the first partition on the first disk
/dev/sd *a* (first disk) *1* (first partition)

/dev/sda2 
/dev/sd *a* (first disk) *2* (second partition)

usually /dev/sda5 is the first logical partition on the disk.

/dev/sdb3 is the third partition on the second disk...

i.e.
```
mount
/dev/sda1 on / type ext3 (rw)
none on /dev type ramfs (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /dev/pts type devpts (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda3 on /home type ext4 (rw)
/dev/sda2 on /mnt/karmic type ext4 (rw)
none on /mnt/karmic/sys type sysfs (rw)
none on /mnt/karmic/proc type proc (rw)
/dev on /mnt/karmic/dev type none (rw,bind)
/dev/pts on /mnt/karmic/dev/pts type none (rw,bind)

```

sda1 is my root ("/") partition
sda3 is my /home partition
and sda2 is the root of my karmic installation.

---

