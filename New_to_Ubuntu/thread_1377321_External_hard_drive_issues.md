---
title: "External hard drive issues"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by KarenAK on 2010-01-10
I used gparted to format a Western Digital hard drive as ext 4 because I got warnings that it was failing.
I labeled it as WD

Issue #1
I have no permission to copy files to the hard drive
How can I change permissions for this hard drive ?

Issue #2
instead of the label WD it is listed as 
/media/f1f17e3a-4b7c-4be2-9715-25c5657ad3e4
How can I change this to a manageable name ?


Thanks in advance for any help :-)

---

### Post by talsemgeest on 2010-01-10
> **KarenAK said:**
> I used gparted to format a Western Digital hard drive as ext 4 because I got warnings that it was failing.
I labeled it as WD

Issue #1
I have no permission to copy files to the hard drive
How can I change permissions for this hard drive ?

Issue #2
instead of the label WD it is listed as 
/media/f1f17e3a-4b7c-4be2-9715-25c5657ad3e4
How can I change this to a manageable name ?


Thanks in advance for any help :-)
For the file permissions, take a look [here](https://help.ubuntu.com/community/FilePermissions), and for mounting the hard drive where you like, first find the device number using ```
sudo fdisk -l
```, create the directory you want the hard drive to be in, something like ```
sudo mkdir /media/WD
``` then, using the device number you found using the first command, mount the hard drive the the directory you created: ```
sudo mount /dev/sdb1 /media/WD
```

---

### Post by aaronp on 2010-01-10
> **KarenAK said:**
> 
Issue #1
I have no permission to copy files to the hard drive
How can I change permissions for this hard drive ?

Issue #2
instead of the label WD it is listed as
/media/f1f17e3a-4b7c-4be2-9715-25c5657ad3e4
How can I change this to a manageable name ?


This looks like your mountpoint (i.e. not drive label) is /media/f1f17e3a-4b7c-4be2-9715-25c5657ad3e4?
If that is the case, create a new directory in /media (e.g. /media/external) 

```
sudo mkdir /media/external
```

You need to change permissions on the new mountpoint.
For example, my hard drives have permissions of drwxrwxr-x and user root, group plugdev.
To make yours the same you can use these commands (assuming your new mountpoint is /media/external)

```

cd /media
sudo chown root external
sudo chgrp plugdev external
sudo chmod 775 external

```


You can then unmount it from the current mountpoint and mount it to your new directory instead. You will need the name of the device though.

Type mount into a terminal and it will list all mounted devices.
Look for the line that has /media/f1f17e3a-4b7c-4be2-9715-25c5657ad3e4 in it and note on the same line it will have something like /dev/sdb1


Then, start with this to unmount it:

```
sudo umount /media/f1f17e3a-4b7c-4be2-9715-25c5657ad3e4 
```

Then this command to mount the drive into the new mountpoint

```
sudo mount /dev/XXXX /media/external
``` where /dev/XXXX is the device name you found earlier.

Now, if it all works, you will want to update your fstab to make it mount there automatically from now on.
Try this tutorial to get this happening:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by KarenAK on 2010-01-10
That was an answer even a newbie like me could understand - so: 

THANK YOU :-)

---

### Post by CharlesA on 2010-01-10
> **aaronp said:**
> 
You need to change permissions on the new mountpoint.
For example, my hard drives have permissions of drwxrwxr-x and user root, group plugdev.
To make yours the same you can use these commands (assuming your new mountpoint is /media/external)

```

cd /media
sudo chown root external
sudo chgrp plugdev external
sudo chmod 775 external

```

I thought you could just use *chown root:plugdev external* instead of using both chown and chgrp. That's how I change owner and groups on my machine.

---

