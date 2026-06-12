---
title: "Help with mounting partitions"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by davidp03 on 2011-05-25
I have three partitions on my HDD: two for OSs--I'm running a dual boot system with XP and Ubuntu 11.04 each on separate partitions--and one for data storage. I would like for the data storage to be my main area for storage for Ubuntu but have two problems.

1. How do I permanently mount the storage partition so that it doesn't have to be mounted every time I boot up?

2. How do I move my user profile and storing instructions to the storage partition?

I'm new to Ubuntu and Linux OSs and am excited to making the switch. Any help is of obvious great appreciation!

dp

---

### Post by deebee19701 on 2011-05-25
mounting and umounting filesystems:

mount -t(type) iso9660 /dev/cdrom(device name) /mnt/cdrom(where you want to mount the cdrom)
       cd /mnt/cdrom to view contents

umount /dev/cdrom or /mnt/cdrom
** device cannot be busy (you are in the directory)


/etc/fstab = filesystem talbe
           - list file system that will be mounted when you boot the computer
           - anything that starts with none is specific to linux
           
/etc/mtab = what devices are mounted on the system and their permission types

---

### Post by noidian on 2011-05-25
What is your ubuntu version?

try this:

Modify fstab and mkdir /media/name
Follow this:
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
Then 
Startup script
write bash script
copy to /etc/init.d
chmod +x ...
update-rc.d FOO defaults or update-rc.d -f chk start 99 2 3 4 5 6 .(for all runlevels

It should work.

---

### Post by seawolf167 on 2011-05-26
To have your "data" partition mount upon boot, you'll need to add an /etc/fstab entry. We can help you format this properly if you provide the output of the following commands

```
sudo blkid
sudo fdisk -l
mount
```

otherwise, if you'd like to try it yourself, take a look at the fstab link in my signature.

As for moving your "user profile", this in the *nix world would be /home (which stores all your application preferences, etc.), you can move this to a different partition by following the instructions [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

---

### Post by 1991sudarshan on 2011-05-26
This is my /etc/fstab file

[B][SIZE=3]UUID=5210A9B810A9A407 /mnt/sda1 ntfs-3g auto 0 0
UUID=b1332f0f-d55b-4082-8350-e17a14c2a316 swap swap sw 0 0
UUID=436111D017CE294A /mnt/sda2 ntfs-3g auto 0 0
UUID=0F75E0010C16ED5B /mnt/sda5 ntfs-3g auto 0 0
UUID=4a616438-6a2f-41c0-9f5a-b9ad54d500f0 / ext4 defaults 0 1
UUID=6AD0D8DA3589C220 /mnt/sda6 ntfs-3g auto 0 0
UUID=349551E454320BE4 /mnt/sda7 ntfs-3g auto 0 0
UUID=6C44538F27B40F61 /mnt/sda8 ntfs-3g auto 0 0
UUID=23E4386C3B553D13 /mnt/sda9 ntfs-3g auto 0 0
kevin@kevin-desktop:~$[/SIZE][/B]

uuid= ---> are the partitions in the hard disk
/mnt/sda1  -----> point where the uuid partitions are mounted 
ntfs-3g,ext4 ------> format of the particular partitions
auto-------->  auto mounting 
noauto -------> no auto mounting


Do not uuid stutfs! Just type the directory where you want to mount the partitions. Initially it will be **noauto**  just change it to[B] auto


[/B]Initially it will be **/media**  will be the mount point for all the partitions and suppose you want to auto mount the partitions create separate directory for each directory 
Ex
/media/partition-1
/media/partition-2
/media/partition-3.....etc

go to the terminal

[B]cd /media
sudo mkdir partition1 partition2 partition3 partition4 ... 

[/B]instead of partion1 partiton2 you can give you own name to the directory

first of all create those directories and then edit /etc/fstab with this command

**sudo gedit /etc/fstab**

---

