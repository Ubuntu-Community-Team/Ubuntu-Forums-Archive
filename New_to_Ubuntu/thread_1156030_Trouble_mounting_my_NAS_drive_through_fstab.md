---
title: "Trouble mounting my NAS drive through fstab"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by notbitmonk on 2009-05-11
I've checked dmizer howto to install a NAS with CIFS and followed it without the credentials part.  With the guest option it gives the following error:
> wrong fs type, bad option, bad superblock on //192.168.1.4/Compartido/Data,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 and had to change guest for user="",pass="" but then it gives me an error that says: can't read superblock
> [ 5466.810920]  CIFS VFS: No username specified
[ 5466.810930]  CIFS VFS: cifs_mount failed w/return code = -22
[ 5505.761112]  CIFS VFS: No username specified
[ 5505.761120]  CIFS VFS: cifs_mount failed w/return code = -22
[ 5562.939640]  CIFS VFS: cifs_mount failed w/return code = -5
[ 5744.156404]  CIFS VFS: No username specified
[ 5744.156414]  CIFS VFS: cifs_mount failed w/return code = -22
[ 5761.401780]  CIFS VFS: No username specified
[ 5761.401787]  CIFS VFS: cifs_mount failed w/return code = -22
[ 5803.231647]  CIFS VFS: cifs_mount failed w/return code = -5

I am able to mount it through gvfs but I do not want to click on the link every time I boot the computer.  Besides, it looks like it loses its connection every now and them and I have to access the drive through Nautilus to get it working again.  At this point I think that I'm closer to getting it to work (mount through fstab).  Any help (Ubuntu 9.04)?

---

### Post by Peter09 on 2009-05-11
I had a similar issue and found the best way was to put a user name and password on the NAS shares and then use a credentials file to mount it.

---

### Post by notbitmonk on 2009-05-12
Will try to do that later in the week and post back the results.

---

