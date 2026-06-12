---
title: "Unable to mount a Synology NAS"
date: 2022-11-07
forum: Networking &amp; Wireless
---

### Post by edvaessen on 2022-11-07
[FONT=arial]Mounting a Synology NAS used to be simple on Ubuntu.
One had to create a mount point and then use a mounting command.
For example:
sudo mkdir /mnt/data1 
sudo mount 192.168.178.2:/volume1/data1 /mnt/data1

At present, with Ubuntu 22.10, this gives errors:

mount: /mnt/data1: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program. 
       dmesg(1) may have more information after failed mount system call.

I followed some advise and typed:

sudo mount -t cifs //192.168.178.2/volume1/data2 /mnt/data2

However, errors again:

mount error(95): Operation not supported 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

[/FONT]Can anyone tell me what to do to get a simple Synology NAS attached to Ubuntu??

---

### Post by TheFu on 2022-11-08
In the last few weeks, there have been a few threads about Synology mounts in 22.10.  I don't have a Synology, but each person was able to solve the issue in their thread. Mostly, it was typos and setting on the Synology side.  Please take a look at those threads and see if they help.  Posting the commands and output requested in the other threads would likely be helpful too. Please, please, please, use forum code-tags.  Some of the output is extremely hard to read without those. Make it easier for people to help you.

BTW, if you use NFS, I can help.  The mount command format is specific, but it hasn't changed in 25 yrs either, but it does need to be correct.

---

### Post by edvaessen on 2022-11-08
Hello TheFu,

The trick was installing nfs-common.
Thanks for your advise.


Regards,

Ed

---

### Post by TheFu on 2022-11-08
Not really a trick.  If you want to use NFS, then the NFS utilities need to be installed.  They aren't pre-installed, since so many home users don't have a clue how great NFS is.  ;)

---

