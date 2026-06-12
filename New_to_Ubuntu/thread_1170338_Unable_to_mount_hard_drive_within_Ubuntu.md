---
title: "Unable to mount hard drive within Ubuntu"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by kaboose72 on 2009-05-26
After curiosity got the better of me I seem to have made one of my hard drives un-mountable.  I did this amazing feat after going:

places > 320.1gb media > right clicking and selecting properties then altering the mounting point information in one of the tabs (it was blank and I entered /media/320gb)

Now when selecting the hard drive the following error appears:

"Cannot mount volume.

Error org.freedesktop.Hal>Device.UnknownError.

Details:
libhal.c 1399 : wrong reply fromhald. Expecting an array. org.freedesktop.Hal.Device.Volume.UnknownFailure"

Is it possible to reverse what I did ? :oops:

---

### Post by allenbradley on 2009-05-26
Have you tried mounting the disk manually? ( Not a solution, just a workaround )

At the terminal, type in :

```
sudo fdisk -l
```

Find the device under which the 320GB hard disk turns up eg. /dev/sdb1 or something like that ( depending on the device you plugged in )

Looking at what you tried to do, I am assuming you want the hard disk to mount under the name 320GB. 
```

cd /media
sudo mkdir 320GB
```

Replace 320GB with any other name you deem fit.

Now, I presume your hard disk is formatted with NTFS. We shall use ntfs-3g to mount the hard disk. It is by default installed in ubuntu. If not, type
```
sudo aptitude install ntfs-3g
```

Now, with ntfs-3g, type
```
sudo ntfs-3g /dev/sdb1 /media/320GB
```

where /dev/sdb1 is the device name from the fdisk command and /media/320GB is the desired mount point you created using mkdir.

Do let me know if it works.

---

### Post by mkrahmeh on 2009-05-26
> **allenbradley said:**
> 
Now, with ntfs-3g, type
```
sudo ntfs-3g /dev/sdb1 /media/320GB
```



i think the command would be
```
sudo mount -t ntfs-3g /dev/sdb1 /media/320GB
```
:popcorn:

ps: notice that you changed the mount point into /media/320gb..maybe the drive became unmountable coz the path does not exist. if so, try to create the directory 320gb before going into the terminal, it might work

---

### Post by allenbradley on 2009-05-26
> **mkrahmeh said:**
> i think the command would be
```
sudo mount -t ntfs-3g /dev/sdb1 /media/320GB
```


> 
from the man page of ntfs-3g

EXAMPLES
       Mount /dev/sda1 to /mnt/windows (make sure /mnt/windows exists):

              ntfs-3g /dev/sda1 /mnt/windows

       or

              mount -t ntfs-3g /dev/sda1 /mnt/windows


so either way..

---

### Post by egalvan on 2009-05-26
Are these paths equivalent?
(I know Unix is case sensitive in many things..
might this be his problem?)

/media/320GB

/media/320gb

---

### Post by kaboose72 on 2009-05-26
> **allenbradley said:**
> Have you tried mounting the disk manually? ( Not a solution, just a workaround )

At the terminal, type in :

```
sudo fdisk -l
```Find the device under which the 320GB hard disk turns up eg. /dev/sdb1 or something like that ( depending on the device you plugged in )

Looking at what you tried to do, I am assuming you want the hard disk to mount under the name 320GB. 
```

cd /media
sudo mkdir 320GB
```Replace 320GB with any other name you deem fit.

Now, I presume your hard disk is formatted with NTFS. We shall use ntfs-3g to mount the hard disk. It is by default installed in ubuntu. If not, type
```
sudo aptitude install ntfs-3g
```Now, with ntfs-3g, type
```
sudo ntfs-3g /dev/sdb1 /media/320GB
```where /dev/sdb1 is the device name from the fdisk command and /media/320GB is the desired mount point you created using mkdir.

Do let me know if it works.

Followed the first example and it works perfectly.  It allows access to the harddrive and the shortcut via the places menu also works again!  Cheers

---

