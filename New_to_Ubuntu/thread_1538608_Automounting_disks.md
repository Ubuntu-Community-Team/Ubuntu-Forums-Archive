---
title: "Automounting disks"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by KWLLC on 2010-07-25
I have just made the jump to use UBUNTU full time, but I have 4 drives that have files I have accumulated from MS all the way back to 6.22 and from my IBM mainframe career.
I wound like to have that media auto-mount at startup. I can't find the correct place to do this.

---

### Post by brujoquizz on 2010-07-25
You have to edit /etc/fstab to manage your disk partitions. There is an easy to use tool called PySDM (go to the Software Center and install it) that allows you to edit the fstab graphically.

More information on: [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by KWLLC on 2010-07-25
OK. I installed pySDM. Looking at the information in the window, I am a bit confused. Is there a man or info file for this tool?

---

### Post by Elfy on 2010-07-25
There is a lot of information here for pysdm. Hope that helps

[http://ubuntuforums.org/showpost.php?p=5470813&postcount=1](http://ubuntuforums.org/showpost.php?p=5470813&postcount=1)

If you want to look into doing it manually 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by snip3r8 on 2010-07-25
i prefer the normal method 
first manually mount the drives that you want to mount on startup

then:
```
df
```here is mine as an example
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             20390688   6799204  12555696  36% /
udev                   1030712       304   1030408   1% /dev
none                   1030712      1840   1028872   1% /dev/shm
none                   1030712       360   1030352   1% /var/run
none                   1030712         4   1030708   1% /var/lock
none                   1030712         0   1030712   0% /lib/init/rw
/dev/sdb2            488282108 158548836 329733272  33% /media/500
/dev/sda5            222524312 130141152  92383160  59% /media/250

```i then edited fstab to look like the following :

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=ef4f07c3-dafe-4d59-870b-2623a1005088 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f759d30f-707f-42ad-b7cd-7fd894d0ae2c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb2    /media/500    ntfs    users,exec,rw    0    0
/dev/sda5    /media/250    ntfs    users,exec,rw    0    0

```so now sdb 2 and 5 mount at /media/500 and /media/250 ,this will be effective on reboot.
remember that you have to create the mount points.so if in fstab you set it to mount at /media/500 the directory /media/500 must exist

---

### Post by KWLLC on 2010-07-25
Thanks to all. I found the doc for pySDM very useful. I'm going to give it a go.

---

