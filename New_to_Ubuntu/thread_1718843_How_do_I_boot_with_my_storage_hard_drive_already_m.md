---
title: "How do I boot with my storage hard drive already mounted?"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Zanderist on 2011-03-31
As the title says, how do I boot into ubuntu with the partition (with all my photos and music) already mounted?

---

### Post by Hedgehog1 on 2011-03-31
typically we add them to the fstab (**F**ile **S**ystem **TAB**le) file:

```
gksudo gedit /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=f2fd03c5-2835-415c-8448-75473daf624a  /                 ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0  
# /home partition was /dev/sda7
UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e  /home             ext4  nodev,nosuid         0  2
[B][COLOR="Red"]# Automount Windows paritions
UUID=EA561004560FCFED                      /media/Area51     ntfs  defaults             0  0  
UUID=5C28DA0E28D9E754                      /media/Area52     ntfs  defaults             0  0 [/COLOR][/B] 
```

The red lines are for NTFS partitons.  You will need to make the directories in the /media directory to match the names you choose for the drive(s).

To find the UUIDs of your drives:

```
sudo blkid -o value -s UUID
```


***The Hedge***

:KS

**EDIT:** I was just a bit faster posting then oldfred tonight...

---

### Post by oldfred on 2011-03-31
You have to create a mount point which can be anything (other than names already used, or delete those names). You then edit fstab to include the partition(s). 

Is the storage drive permanent? Is it NTFS or a Linux format? Exact instructions will be different depending.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

You can directly mount them into /home. I prefer to mount in /mnt/data (they do not show twice in the left panel) and then link all my folders in /data into /home.

---

### Post by Zanderist on 2011-03-31
EDIT: never mind, I decided to mount the storage partition and watch where gparted reported where it mounted. I now have my mount point defined.

> To find the UUIDs of your drives:

```
sudo blkid -o value -s UUID
```I did that, and was pretty confused, so I found a better way of finding the UUID with gparted. 

Just right click and go to info. it should be listed.

EDIT2: Okay thanks guys I got it to work.

---

### Post by Hedgehog1 on 2011-04-01
> **Zanderist said:**
> I did that, and was pretty confused, so I found a better way of finding the UUID with gparted. 

Just right click and go to info. it should be listed.

**OH Sure** - if you want to do it the **NON-NERD** way! :D

Glad you are operational!

***The Hedge***

:KS

---

