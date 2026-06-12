---
title: "Problems mounting windows partition"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Ant01 on 2009-02-07
Please can someone assist:(

I am having problems mounting a windows partition in ubuntu. The partition was mounted and working and then something happened. I loaded the drive via windows and reformated it with the hope that it would mount. I first ran sudo fdisk -l then, 
the mount command (sudo mount /dev/sdb1 /media/sdb1)
it seems to mount, but when I look at computer directory I can't see the mounted directory

I also tried running the ntfs repair command
sudo aptitude install ntfsprogs
ntfsfix /dev/partition.name

---

### Post by taurus on 2009-02-07
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by Ant01 on 2009-02-07
> **taurus said:**
> What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

I get the following outputs
[IMG]http://www.mydivealbum.com/userfiles/ubuntuprtscn.jpg[/IMG]

---

### Post by taurus on 2009-02-07
Looks like both of your ntfs partitions are already mounted, /dev/sda1 to /media/drive2 & /dev/sdb1 to /media/48gig.

Do you now want to mount the other linux partition, /dev/sdb2?

```
sudo mkdir /media/sdb2
sudo mount -t ext3 /dev/sdb2 /media/sdb2
df -h
```

---

### Post by Ant01 on 2009-02-07
> **taurus said:**
> Looks like both of your ntfs partitions are already mounted, /dev/sda1 to /media/drive2 & /dev/sdb1 to /media/48gig.

Do you now want to mount the other linux partition, /dev/sdb2?

```
sudo mkdir /media/sdb2
sudo mount -t ext3 /dev/sdb2 /media/sdb2
df -h
```

Thats what I thought, but I can't see the partition for the 48gig in my computer directory

[IMG]http://www.mydivealbum.com/userfiles/ubuntuprtscn2.jpg[/IMG]

---

### Post by taurus on 2009-02-07
Minimize the Computer window.  Do you see an icon for the 48gig drive on your desktop?

---

### Post by Ant01 on 2009-02-07
No, there isn't

---

### Post by artsci2 on 2009-02-07
I just went through some of these problems. The solution was to use SUPERAntiSpyware on the windows hard drive. After that run the hard drive is accessible to my Ubuntu 8.10 system.

([http://www.superantispyware.com/?tag=GOOGLE-SUPERANTISPYWARE](http://www.superantispyware.com/?tag=GOOGLE-SUPERANTISPYWARE))

---

### Post by Ant01 on 2009-02-07
> **artsci2 said:**
> I just went through some of these problems. The solution was to use SUPERAntiSpyware on the windows hard drive. After that run the hard drive is accessible to my Ubuntu 8.10 system.

([http://www.superantispyware.com/?tag=GOOGLE-SUPERANTISPYWARE](http://www.superantispyware.com/?tag=GOOGLE-SUPERANTISPYWARE))

I'll try that although I can't understand it as I reformated the partition in windows, there is nothing on that partition and ubuntu can mount and see the other windows partitions. Thanks anyway, I see what happens

---

### Post by taurus on 2009-02-07
```
ls -la /media/48gig
```

---

### Post by Hendrixski on 2009-02-07
Not to ask the obvious but... what do you still need Windows for?  

If you're mounting that section to work on files, or to get added space then just delete Windows and you'll have all the files on Linux and you'll have more free space.

---

