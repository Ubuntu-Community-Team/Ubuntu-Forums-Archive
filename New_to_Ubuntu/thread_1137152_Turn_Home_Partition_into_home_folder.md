---
title: "Turn Home Partition into /home folder"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by BlueCanary9999 on 2009-04-25
When installing Intrepid I was decided to make a separate home partition in case I need to reinstall Ubuntu or want to do a fresh install of Jaunty.  Conveniently, the /home folder in Intrepid was the partition.  But I recently installed Jaunty, and now I have a new, blank /home folder.  I have to access my home partition through "138.0 GB Media," which is tedious, especially when programs will be automatically using the now-blank /home folder instead of the partition.  How can I make the partition the home folder?  Thanks for your time!

---

### Post by lovelyvik293 on 2009-04-25
You can mount the "138.0 GB Media" at your /home folder or inside /home folder as a subfolder by editing your /etc/fstab file.

---

### Post by BlueCanary9999 on 2009-04-25
Thanks.  But I'm a Linux noob, what would I edit?  If this helps at all, here is the text of /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=067f81c2-d1f2-401f-8966-f051b5434fa4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1751cac6-ca02-4dfe-830c-051fc9335206 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by lvleph on 2009-04-25
What you are going to need to do is add the mount:
```

UUID=<YOUR UUID> /home           ext3    relatime        0       2
```

The UUID for the drive can be found using blkid in terminal.

EDIT: If you want, just post the output of blkid here and someone can post the line that needs to be added to fstab.

---

### Post by BlueCanary9999 on 2009-04-25
Will do, thank you.  Here's the blkid text:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A81EE8FF1EE8C780" TYPE="ntfs" 
/dev/sda3: UUID="88645A71645A624C" TYPE="ntfs" 
/dev/sda5: UUID="157801C99131C034" LABEL="LENOVO" TYPE="ntfs" 
/dev/sda6: UUID="1751cac6-ca02-4dfe-830c-051fc9335206" TYPE="swap" 
/dev/sda7: UUID="067f81c2-d1f2-401f-8966-f051b5434fa4" TYPE="ext3" 
/dev/sda8: UUID="f14da533-f855-4b97-b5b2-b1db1b63c4d9" SEC_TYPE="ext2" TYPE="ext3" 

I don't remember whether 7 or 8 is the home folder.... If there was a way to check the storage of each, I could figure it out.  is there?  Or can you tell from SEC_TYPE="ext2"?

---

### Post by lvleph on 2009-04-25
Here you go, it was /dev/sda8
```

UUID=f14da533-f855-4b97-b5b2-b1db1b63c4d9 /home           ext3    relatime        0       2

```

---

### Post by lvleph on 2009-04-25
Sorry, I forgot to say you will need to also run
```
sudo mount -a
```
in the terminal after you edit fstab. If that doesn't get the home drive mounted correctly then restart. Oh and I could tell which was the home partition from the fact that it was the only ext3 not in fstab.

---

### Post by BlueCanary9999 on 2009-04-25
:O

Thanks you so much!  :D

---

### Post by 67GTA on 2009-04-25
The next time you install, choose manual partitioner, tell it to mount your home partition as /home but NOT TO FORMAT IT(just mount). Make sure to choose the correct filesystem to be used as (ext3,ext4,etc..) Make sure to use same username/password as you already have, and it will be exactly as you wanted.

---

### Post by lvleph on 2009-04-25
And if you do it that way, you would almost not realize you reinstalled (missing programs aside).

---

