---
title: "Cant see hard drive"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by dontgetshocked on 2006-11-07
For some reason I cant see my other hard drive which has both linux and widows on it partitioned! I have 2 80gig drives, one with Ubuntu on it which is my main boot drive and is up and running now and the other secondary drive which has the os's on it. The other drive isnt seen either thru network servers or computers. What can i do?

---

### Post by taurus on 2006-11-07
You probably need to mount it before you can acess or "see" it!  What are the output of these two commands, from a terminal (Applications -> Accessories -> Terminal).  

```
sudo fdisk -l
more /etc/fstab
```
Otherwise, read this...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dontgetshocked on 2006-11-07
atic file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdf1 -- converted during upgrade to edgy
UUID=affd439c-e5f4-449b-bff1-51550e3a0334 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdf5 -- converted during upgrade to edgy
UUID=01296063-2cf7-41dd-83bd-377905135cab none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
_____________________________________________________________________________
Disk /dev/hdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1        9351    75111876   83  Linux
/dev/hdf2            9352        9729     3036285    5  Extended
/dev/hdf5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1        6043    48540366    7  HPFS/NTFS
/dev/hdg2            6044        9575    28370790   83  Linux
/dev/hdg3            9576        9729     1237005    5  Extended
/dev/hdg5            9576        9729     1236973+  82  Linux swap / Solaris

---

### Post by taurus on 2006-11-07
So I assume you want to mount /dev/hdg1 then.  You need to edit your /etc/fstab and add an entry to mount it each time you boot your Ubuntu.  You can edit /etc/fstab by (from a terminal again)

```

sudo cp /etc/fstab  /etc/fstab.bak  <-- make a backup copy just in case...
gksudo gedit /etc/fstab
```
Now, add the following line to the end of it.

```

/dev/hdg1   /media/windows   ntfs   defaults,umask=0222   0   0

```
Save it and run the next three commands.

```

sudo mkdir /media/windows  <-- create a mount point for it
sudo mount -a  <-- mount it
df -h  <-- you should see your XP in /media/windows now

```

---

### Post by dontgetshocked on 2006-11-07
One more thing please. It says the drive is read only, how can I change this? I tried doing it thru right click and permissions as root but this didnt work.

---

### Post by kinematic on 2006-11-07
you need to install the ntfsg3 driver to write safely to it with linux.
you'll have to do a forum search because i don't have a ntfs partition so i can't offer any further help.

---

### Post by taurus on 2006-11-07
> **dontgetshocked said:**
> One more thing please. It says the drive is read only, how can I change this? I tried doing it thru right click and permissions as root but this didnt work.

Here you go...

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

