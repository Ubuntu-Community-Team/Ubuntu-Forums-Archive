---
title: "Help: Have copied exsisting installation to Larger HD .."
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Grendyl on 2009-08-08
.. and everything boots ok, I can see the new larger "free" area on the disk, but can't write anything to it unless I am in Root .. so I have 98GB that I can't use, as a complete newbie can someone explain in plain English how I can make this free space available when logged in as non-root.

GParted shows the structure as follows;

Partition : /dev/sda1 (also has what looks like a set of keys next to it)
file system : ext3
mount point : /
size : 39.06 GiB
Used : 10.33 GiB
Unused : 28.73 Gib
Flags : boot

Partition : /dev/sda2 (also with keys)
file system : extended
mount point :
size : 109.99 GiB
Used : ....
Unused : ....
Flags : 

Within that extended partition is the following;

Partition : /dev/sda5
file system : linux-swap
mount point : 
size : 10.12 GiB
Used : ....
Unused : ....
flags :

Partiton : /dev/sda6 (also with keys)
file system : ext3
mount point : /media/disk
size : 99.87 GiB
used : 1.75 GiB
Unused : 98.12 GiB
flags : 

I'm assuming i've done something wrong when cloning my old 40 GiB main drive onto this new one.

Screen shot attached.

---

### Post by mikewhatever on 2009-08-08
Are you trying to run Ubuntu from sda6, or do you want to use sda6 for file storage?

---

### Post by drs305 on 2009-08-08
Make a mountpoint for sda6 and make yourself the owner:
```

sudo mkdir /media/*yourmountpoint*
sudo chown -R *yourusername:* /media/yourmountpoint

```

Add the entry to fstab:
```

sudo cp /etc/fstab /etc/fstab.bak  # Make backup
gksudo gedit /etc/fstab

```

Add this line:
> 
/dev/sda6 /media/yourmountpoint ext3 defaults,user 0 2


Unmount /dev/sda6 then remount. If you don't see anything on the second command, it's mounted:
```

sudo umount /dev/sda6
sudo mount /dev/sda6

```

Notes:
Instead of using /media as the mountpoint, you might want /mnt if you don't want to see the mountpoint on the Desktop.
You may prefer using a UUID in fstab instead of /dev/sda6. To get the UUID:
```

sudo blkid | grep /dev/sda6

```
Then replace "/dev/sda6" with "UUID=XXXXXXXXXXXXXX" (i.e. the UUID from the command).

Here is a good link on fstab;
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

And Permissions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by Grendyl on 2009-08-08
> **mikewhatever said:**
> Are you trying to run Ubuntu from sda6, or do you want to use sda6 for file storage?


No Ubuntu is on Sda1, i want sda6 for just storage

---

### Post by Grendyl on 2009-08-08
> **drs305 said:**
> Make a mountpoint for sda6 and make yourself the owner:
```

sudo mkdir /media/*yourmountpoint*
sudo chown -R *yourusername:* /media/yourmountpoint

```

Add the entry to fstab:
```

sudo cp /etc/fstab /etc/fstab.bak  # Make backup
gksudo gedit /etc/fstab

```

Add this line:


Unmount /dev/sda6 then remount. If you don't see anything on the second command, it's mounted:
```

sudo umount /dev/sda6
sudo mount /dev/sda6

```

Notes:
Instead of using /media as the mountpoint, you might want /mnt if you don't want to see the mountpoint on the Desktop.
You may prefer using a UUID in fstab instead of /dev/sda6. To get the UUID:
```

sudo blkid | grep /dev/sda6

```
Then replace "/dev/sda6" with "UUID=XXXXXXXXXXXXXX" (i.e. the UUID from the command).

Here is a good link on fstab;
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

And Permissions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")


Followed your lesson to the letter, but still saying I don't have permission to write to it ..

---

### Post by drs305 on 2009-08-08
> **Grendyl said:**
> Followed your lesson to the letter, but still saying I don't have permission to write to it ..

With it mounted, please post:
```

mount
ls -la /media/*mountpoint*

```

By the way, the "set of keys" in gparted is the symbol that the partition is mounted...

---

### Post by Grendyl on 2009-08-08
total 24
drwxr-xr-x 3 root   root    4096 2009-08-08 20:28 .
drwxr-xr-x 7 fugazi fugazi  4096 2009-08-09 01:40 ..
drwx------ 2 root   root   16384 2009-08-08 20:28 lost+found

---

### Post by drs305 on 2009-08-08
Some of the folders are still owned by root. If these are all data files, and you want to own them, you can safely change the ownership to yourself with (assuming your username is fugazi). With /dev/sda6 mounted, run:
```

sudo chown -R fugazi: /media/*yourmountpoint*

```

---

### Post by Grendyl on 2009-08-08
> **drs305 said:**
> Some of the folders are still owned by root. If these are all data files, and you want to own them, you can safely change the ownership to yourself with (assuming your username is fugazi). With /dev/sda6 mounted, run:
```

sudo chown -R fugazi: /media/*yourmountpoint*

```

Still no go

---

### Post by mikewhatever on 2009-08-08
> **Grendyl said:**
> No Ubuntu is on Sda1, i want sda6 for just storage

So what's the deal with 'copied **exsisting installation** to Larger HD'?

All you had to do was chown the already existing mount point for sda6, but now things are kind of messy, If it still doesn't work for you, post the output of the following commands:
df -h
cat /etc/fstab

---

### Post by drs305 on 2009-08-08
This issue was resolved earlier, in part outside this thread. 

The OP wanted the mount point as /media/data and we created an appropriate fstab entry and mount point, chown/chmod'd the current folders and files, and remouted everything.

---

### Post by Grendyl on 2009-08-09
> **drs305 said:**
> Some of the folders are still owned by root. If these are all data files, and you want to own them, you can safely change the ownership to yourself with (assuming your username is fugazi). With /dev/sda6 mounted, run:
```

sudo chown -R fugazi: /media/*yourmountpoint*

```

Thank you drs305, everything working fine now :)

---

### Post by Grendyl on 2009-08-09
> **Grendyl said:**
> Thank you drs305, everything working fine now :)

Oh and these were the commands that finally did it

Added fstab entry.
sudo mkdir /media/data
sudo umount /dev/sda6 # unmounts sda6
sudo mount -a # mounts all fstab entries
sudo chown -R yourusername: /media/data # make you owner
chmod 750 -R /media/data

---

