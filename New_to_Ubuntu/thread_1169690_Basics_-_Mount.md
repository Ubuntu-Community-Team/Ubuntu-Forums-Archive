---
title: "Basics - Mount"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by lile001 on 2009-05-25
I have two hard drives.  When I was setting up ubuntu, I believe I said to mount the second drive under /home as the drive was being formatted.  I figured that I could copy things from one drive to another this way, for quick backups.  

Well, I'm not sure how to tell whether this was successful or not.  I can't see anything in the graphical user interface that seems to indicate there is anything like an extra drive under /home.  If i right click and choose properties for /home it says there is 185GB free, however if there is another drive in there it should have about 300GB free.  This seems to indicate that I wasn't successful at doing this, or I don't have any idea what I should be seeing.  

How can I proceed to figure out if that second drive exists, if I didn't make some mistake during install, and where it is located?  Don't know much about Ubuntu at all, so I don't even know the right question to ask in a help file.

---

### Post by taurus on 2009-05-25
Open a terminal and post the outputs of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by cariboo on 2009-05-25
The quick way to find what partitions are on what drive, is to open an Applications-->Accessories-->Terminal and type:

```
df -h
```

you should get something similar to this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             5.5G  4.4G  915M  83% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  320K  1.5G   1% /dev
tmpfs                 1.5G   80K  1.5G   1% /dev/shm
/dev/sdb6             108G   22G   81G  22% /home
/dev/sda1             151G  112G   32G  79% /home/storage
/dev/sdb2             108G  8.9G   94G   9% /home/internal
```

as you can see my / partition is on /dev/sdb5 and /home is on /dev/sdb6.

---

### Post by lile001 on 2009-05-25
Applications -> Accessories -> Terminal
[code]sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc62bc62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38912   210162330    f  W95 Ext'd (LBA)
/dev/sda5           12749       38912   210162298+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24d824d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       38913   210170362+   5  Extended
/dev/sdb5           12749       12991     1951866   82  Linux swap / Solaris
/dev/sdb6           12992       38913   208218433+  83  Linux


sudo blkid

/dev/sda1: UUID="F814C97314C93602" TYPE="ntfs" 
/dev/sda5: UUID="07ec0d32-ee44-4b55-ab23-7a2b22ce6457" TYPE="ext3" 
/dev/sdb1: UUID="CA4475D94475C8A9" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="9a4df942-f218-4f18-a123-4d8989d6fe46" 
/dev/sdb6: UUID="93824a50-c6f0-4cbf-85a7-a72f02ea8d47" TYPE="ext3" 


cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=07ec0d32-ee44-4b55-ab23-7a2b22ce6457 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=93824a50-c6f0-4cbf-85a7-a72f02ea8d47 /home           ext3    relatime        0       2
# /windows was on /dev/sdb1 during installation
UUID=CA4475D94475C8A9 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=9a4df942-f218-4f18-a123-4d8989d6fe46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             198G  2.7G  185G   2% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
varrun               1006M  116K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M  164K 1006M   1% /dev
tmpfs                1006M  228K 1006M   1% /dev/shm
lrm                  1006M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb6             196G  602M  185G   1% /home
/dev/sdb1              98G   19G   80G  19% /windows

---

### Post by lile001 on 2009-05-25
So it looks like, if I understand this correctly, /home is equal to the second hard , sdb6 (OK, there's also an NTFS partition with Windows in it, and some other stuff)  and / is equal to the first hard drive, sda5.  

What I was trying to accomplish was something different.  I want to have a place that I can just copy backups to that second drive,  Right now it looks liek I have 180+ GB for the Ubuntu program files, and another 180+ GB under /home.  Hmmm....

---

### Post by lile001 on 2009-05-25
Or maybe this will work.  Is there a simple way to make a place for these backups on sda5?

---

### Post by taurus on 2009-05-25
/dev/sda5 is your root partition so unless you want to resize it, splitting it into two partitions, you could create a backup directory in /media if you wish.  Then, change the ownership of that directory from root to your login name so you can write to it anytime you want.

---

### Post by lile001 on 2009-05-25
> **taurus said:**
> /dev/sda5 is your root partition so unless you want to resize it, splitting it into two partitions, you could create a backup directory in /media if you wish.  Then, change the ownership of that directory from root to your login name so you can write to it anytime you want.

Ok.  I have a vague idea how to go about making a directory in /media.  Got any suggestions?

---

### Post by taurus on 2009-05-25
You mean something like

```
sudo mkdir /media/backup
sudo chown -R username:username /media/backup
```
Replace username with your login name.  Then, you would be the owner of the new directory, /media/backup.

---

### Post by lile001 on 2009-05-25
> **taurus said:**
> You mean something like

```
sudo mkdir /media/backup
sudo chown -R username:username /media/backup
```Replace username with your login name.  Then, you would be the owner of the new directory, /media/backup.


That worked OK! 

Now, I want two different users to be able to save a file in a folder that isn't in thier home directory.  Either this will be /media/backup or a new directory I made called /home/Shared    

I've done several things, none of which seemed to work:

1. Start Nautilus by typing gksu nautilus.  Change permissions in my /home/Shared folder so that people in group users can read and write files.  Add some people to the group users.  When I'm logged in as one of those people, however, can't save a file in /Shared.

2.  Did the following:

      sudo chgrp users Shared
      sudo chmod g+rwx Shared

After this, still can't save files in Shared when I am logged on as one of the people in users.  

Hmm.  I'm not understanding this,  both of those actions should have allowed people in that group to access this direcrtory.  What am I missing?

---

### Post by taurus on 2009-05-25
What's the output of this command?

```
ls -la /home
```

---

### Post by lile001 on 2009-05-25
> **taurus said:**
> What's the output of this command?

```
ls -la /home
```
drwxr-xr-x  7 root    root     4096 2009-05-25 15:18 .
drwxr-xr-x 22 root    root     4096 2009-05-24 20:19 ..
drwxr-xr-x 29 larry   larry    4096 2009-05-25 15:58 larry
drwxr-xr-x 33 larry0  larry0   4096 2009-05-25 15:40 larry0
drwx------  2 root    root    16384 2009-05-24 20:12 lost+found
drwxr-xr-x 29 qhyrrae qhyrrae  4096 2009-05-25 13:22 qhyrrae
drwxrwx---  3 root    users    4096 2009-05-25 15:44 Shared

---

### Post by taurus on 2009-05-25
You can try something like

```
sudo chmod 777 /home/Shared
ls -la /home
```

---

### Post by lile001 on 2009-05-25
> **taurus said:**
> You can try something like

```
sudo chmod 777 /home/Shared
ls -la /home
```

This time it is

drwxrwxrwx  3 root    users    4096 2009-05-25 15:44 Shared

The only difference is rights for "others not in the file's group", but now I can save files there. .  Since my login is part of a group that "owns" this directory, it's hard to understand what is going on.  This shouldn't have been any different than

chmod g+rwx

Obviously I still don't understand this permissions stuff...

---

