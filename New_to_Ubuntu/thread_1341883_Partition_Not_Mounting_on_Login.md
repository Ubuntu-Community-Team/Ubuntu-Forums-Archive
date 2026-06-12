---
title: "Partition Not Mounting on Login"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by kolaperumal on 2009-11-30
hi frnds,
I am bit new to ubuntu .Whenever i login using my user account in Ubuntu, my data partitions are locked and i have to enter the password to unlock them.Is there any way which can unlock my data partition automatically when i log into my system.

---

### Post by SlugSlug on 2009-11-30
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by ukripper on 2009-11-30
> **kolaperumal said:**
> hi frnds,
I am bit new to ubuntu .Whenever i login using my user account in Ubuntu, my data partitions are locked and i have to enter the password to unlock them.Is there any way which can unlock my data partition automatically when i log into my system.

post output of the follwoing commands:

```
sudo blkid
```

```
df -h
```

---

### Post by kolaperumal on 2009-11-30
@UK Ripper
Output for sudo blkid
/dev/loop0: UUID="7440796f-026b-435b-a070-26a8dd7a319f" TYPE="ext4" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0913" TYPE="vfat" 
/dev/sda2: UUID="6804-8C28" TYPE="vfat" 
/dev/sda5: UUID="C678AA5A78AA494F" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="2AD08320D082F0FD" LABEL="DATA" TYPE="ntfs" 

Ouput for df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            7.5G  2.8G  4.3G  40% /
udev                 1007M  288K 1007M   1% /dev
none                 1007M  220K 1007M   1% /dev/shm
none                 1007M  120K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda5             9.8G  8.7G  1.2G  89% /host
/dev/sda6              26G  9.5G   17G  37% /media/DATA

---

### Post by ukripper on 2009-11-30
open terminal and run below command:
```
sudo apt-get install ntfs-config
```

go to System-->Administration--> NTFS configuration tool

and check both boxes press ok. It should mount automatically on every reboot now. if it doesn't post output of below command:
```
gedit /etc/fstab
```

---

### Post by wirate on 2009-11-30
+1 for ntfs configuration tool

---

### Post by kolaperumal on 2009-11-30
@ukripper
Thanks a lot ! :-) Problem Solved.

---

### Post by frncz on 2009-11-30
> **ukripper said:**
> open terminal and run below command:
```
sudo apt-get install ntfs-config
```

go to System-->Administration--> NTFS configuration tool

and check both boxes press ok. It should mount automatically on every reboot now. if it doesn't post output of below command:
```
gedit /etc/fstab
```

Is there anything equivalent for a FAT32 disk?

---

### Post by ukripper on 2009-11-30
Great i am glad it worked out for you. Please mark this thread as solved from thread tools.

> **frncz said:**
> Is there anything equivalent for a FAT32 disk?

not which i am aware of but it is very simple to mount from fstab. post output of below comamnd:
```
sudo blkid
```

```
df -h
```

---

### Post by frncz on 2009-11-30
> **ukripper said:**
> Great i am glad it worked out for you. Please mark this thread as solved from thread tools.



not which i am aware of but it is very simple to mount from fstab. post output of below comamnd:
```
sudo blkid
```

```
df -h
```

OK, thanks. See below

sudo blkid
/dev/sda1: UUID="5edc0bae-3414-42ab-bfb4-72f9c1dcd8e5" TYPE="ext4" 
/dev/sda5: UUID="44ab0bcd-ecee-4a84-b0d0-8167fb6541e1" TYPE="swap" 
/dev/sdb1: LABEL="" UUID="4870-A8A0" TYPE="vfat" 
/dev/sdc1: UUID="82EC760DEC75FC2B" LABEL="bs-mf19" TYPE="ntfs" 
/dev/sdf1: SEC_TYPE="msdos" LABEL="" UUID="8972-18D9" TYPE="vfat" 

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  5.0G  133G   4% /
udev                  500M  328K  500M   1% /dev
none                  500M  196K  500M   1% /dev/shm
none                  500M  324K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock
none                  500M     0  500M   0% /lib/init/rw
/dev/sdb1             466G  157G  309G  34% /media/4870-A8A0
/dev/sdc1              75G   15G   61G  20% /media/bs-mf19
/dev/sdf1             490M  2.0M  488M   1% /media/8972-18D9

 It is sdb1 which I wish to automount. sdf1 is a usb memory stick. 

Thanks

---

### Post by ukripper on 2009-11-30
> **frncz said:**
> OK, thanks. See below

sudo blkid
/dev/sda1: UUID="5edc0bae-3414-42ab-bfb4-72f9c1dcd8e5" TYPE="ext4" 
/dev/sda5: UUID="44ab0bcd-ecee-4a84-b0d0-8167fb6541e1" TYPE="swap" 
/dev/sdb1: LABEL="" UUID="4870-A8A0" TYPE="vfat" 
/dev/sdc1: UUID="82EC760DEC75FC2B" LABEL="bs-mf19" TYPE="ntfs" 
/dev/sdf1: SEC_TYPE="msdos" LABEL="" UUID="8972-18D9" TYPE="vfat" 

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  5.0G  133G   4% /
udev                  500M  328K  500M   1% /dev
none                  500M  196K  500M   1% /dev/shm
none                  500M  324K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock
none                  500M     0  500M   0% /lib/init/rw
/dev/sdb1             466G  157G  309G  34% /media/4870-A8A0
/dev/sdc1              75G   15G   61G  20% /media/bs-mf19
/dev/sdf1             490M  2.0M  488M   1% /media/8972-18D9

 It is sdb1 which I wish to automount. sdf1 is a usb memory stick. 

Thanks

ok first of all let's create a directory for your fat32 to mount on:
```
sudo mkdir /media/fat-drive
```

now add mount point in fstab:

```
sudo gedit /etc/fstab
```

and right at the bottom of file just copy/paste this:
```
UUID=4870-A8A0         /media/fat-drive   vfat   user,fmask=0111,dmask=0000   0   0
```

That's it. save and exit. reboot and check if it mounts.

---

### Post by frncz on 2009-11-30
Thanks ukripper. Your modification to fstab works fine.

---

### Post by ukripper on 2009-11-30
> **frncz said:**
> Thanks ukripper. Your modification to fstab works fine.

Great! Have fun mate.

---

### Post by frncz on 2009-12-04
Hi 

with a few days use, I now realise that all files in fat-drive belong to root and even with sudo chown user filename, I cannot change them back to user, as they were when they were under /media/4870-A8A0. 

my fstab line looks like:
UUID=4870-A8A0         /media/fat-drive   vfat user,fmask=0111,dmask=0000   0   0

When I comment out this line and reboot, I get back to where I used to be. the disk needs mounting by entering password, but the files belong to me again.
Is there something not quite right in the /etc/fstab line?

Thanks

Mike

---

### Post by ukripper on 2009-12-04
> **frncz said:**
> Hi 

with a few days use, I now realise that all files in fat-drive belong to root and even with sudo chown user filename, I cannot change them back to user, as they were when they were under /media/4870-A8A0. 

my fstab line looks like:
UUID=4870-A8A0         /media/fat-drive   vfat user,fmask=0111,dmask=0000   0   0

When I comment out this line and reboot, I get back to where I used to be. the disk needs mounting by entering password, but the files belong to me again.
Is there something not quite right in the /etc/fstab line?

Thanks

Mike

You have to understand linux permissions don't work on Fat or ntfs partitions. if you want permissions and ACL applied, you need to format it in linux recognised filesystems such as ext2/ext3/ext4 such as..

All you can do is block access for some users not to have access to your Fat drive through fstab by chnaging fmask=0177,dmask=0077,uid=1000 thats about it. 

So in that respect it doesn't matter if root is the owner or yourself, as long it is partioned as FAT format.
Here is a good thread to understand more about formats:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

