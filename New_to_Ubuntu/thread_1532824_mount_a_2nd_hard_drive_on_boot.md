---
title: "mount a 2nd hard drive on boot"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by wlraider70 on 2010-07-17
I have a 2nd hard drive in my box. when i start up it is seen, but not mounted. when i give i my password it mounts, but with a long hex looking name.

How can i make it  mount on boot, and with a normal name?

---

### Post by Elfy on 2010-07-17
Add it to fstab after creating a folder to mount it in 

A mount in /mnt will not show on the desktop, a mount in /media probably will.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You could alos install pysdm which will allow you to do so without editing fstab yourself.

---

### Post by garvinrick4 on 2010-07-17
As previous post:
 You can make a label in gparted or disk utility.
Then it will have "a normal name" what ever you want to label it.
I prefer to give all my partitions a label. As below, They are then
mounted in /media/"label"
If I want to mount lets say from below redhat:
Make a directory
```
sudo mkdir /media/redhat
```mount the drive
```
sudo mount /dev/sda9 /media/redhat
```Unmount drive not a typo:
```
sudo umount /media/redhat
```We are just mounting with with label instead of UUID #

rick@rick-laptop:~$ sudo blkid (small case L second letter)
[sudo] password for rick: 
/dev/sda1: LABEL="SYSTEM" UUID="C6EECCF3EECCDCB5" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="66B0BDBFB0BD95D1" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda6: LABEL="lucid" UUID="d03f894f-94ce-4c00-9c43-19c25f2af12c" TYPE="ext4" 
/dev/sda7: LABEL="home" UUID="0f7c5de9-c3b4-4c50-b288-d34e9ef6e119" TYPE="ext4" 
/dev/sda8: LABEL="DATA" UUID="267C-BED1" TYPE="vfat" 
/dev/sda9: LABEL="redhat" UUID="928df639-e6cf-4c3b-9c17-965a91e60efc" TYPE="ext4" 
/dev/sda5: LABEL="maverick" UUID="10f25c5b-a306-4546-b02f-87a1664b5c05" TYPE="ext4" 
This was just for making a label and using it to mount not auto mounting.

---

### Post by wlraider70 on 2010-07-17
thanks

---

