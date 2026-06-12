---
title: "Permissions for brand new HDD"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by DNCashman on 2010-03-18
Hi folks,

Just purchased a Seagate 500GB SATA drive! I formatted it using gParted with the Ext3 file system for compatability with a WinXP vbox installation.

You have to bare with me, I just installed Ubuntu yesterday so am quite new to all this. I realised I cannot create a single folder on the drive. Furthermore, I am required to enter my password to "mount" it. Is there any way I can just make it an drive like my OS drive where I can have all the permissions to do whatever with the drive (as its for storage) and I do not require authentication to access it?

Any suggestions greatly appreciated.

DNCa$hman.

---

### Post by wjm on 2010-03-18
By default Ubuntu forces (strongly encourages) users to make use of the "sudo" system since there is no real "root" to speak of in Ubuntu.  If you can't execute a command because you don't have the right acccess, you can always use sudo to execute it (in fact Ubuntu will suggest you do this all of the time).

example:

sudo mkfs.vfat /dev/sdb1

See Also: [http://ubuntuforums.org/showthread.php?t=261204](http://ubuntuforums.org/showthread.php?t=261204)

---

### Post by DNCashman on 2010-03-18
Found this issue, I didnt give the drives the required permissions. :)

---

### Post by srs5694 on 2010-03-18
You may be interested in creating an /etc/fstab entry for the drive to mount it somewhere convenient (such as within your home directory, if it's for your personal use alone). Load the /etc/fstab file into your favorite editor (you'll need to execute it with sudo, as described by others in this thread) and add an entry similar to this:

```

/dev/sdb1  /home/foo/storage   ext3    defaults        0       2

```

Change /dev/sdb1 to the device filename associated with the drive's single partition and change /home/foo/storage to wherever you want to mount it. That directory must exist (it should be just an empty directory). You can even mount it as /home, although that will require moving your current /home directory tree. Instead of specifying the device filename (/dev/sdb1 in this example), you can use a UUID to specify the device, similar to most entries you've already got in /etc/fstab. Use the blkid command to find the UUID for a device, as in "sudo blkid /dev/sdb1" to find the UUID for /dev/sdb1. Using a UUID makes the configuration more robust against certain types of system changes, such as repartitioning, but it's harder to read in /etc/fstab.

With these changes made, unmount the drive if it's already mounted, then type "sudo mount -a". Your drive should appear in the location you've specified.

---

### Post by DNCashman on 2010-03-18
Sweet, done that too and now its auto mounting.

Excellent :)

---

### Post by Jarmen_Deffs on 2010-03-18
> **DNCashman said:**
> Sweet, done that too and now its auto mounting.

Excellent :)

You'll find that you aren't the owner of the disk though, and so may not have permissions to everything you want.

To fix that change "defaults" in the fstab entry to "defaults,user"

---

