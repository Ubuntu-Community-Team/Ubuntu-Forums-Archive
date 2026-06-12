---
title: "Mount Ubuntu NTFS to Ubuntu NTFS share"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by chrishowell on 2008-11-09
I've looked for days with no answer. 

I have 2 Ubuntu boxes. Each has several NTFS partitions that are shared through SAMBA.


svr1  drive1
svr1  drive2

svr2  drive1
svr2  drive2


From svr1, how can I mount /svr2/drive1 on svr1?  I've tried everything that I can find without success.

Thanks,
Chris

---

### Post by Iowan on 2008-11-09
HAve you seen [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo") one or [this]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html") one?

---

### Post by chrishowell on 2008-11-10
Thanks for the reply.

I tried both and got the same error messages;
  "exportfs: Warning: /media/svr1C does not support NFS export"

After some googling, I have the impression that NTFS partitions can't be exported. 

I have Samba, ntfs-3g and NFS all installed. It seems like the only answer is to move data around and reformat the partitions to ext3 (but the thought of having to move close to 1 tb of files gives me a migraine :frown:

Any other ideas?  

tia,
Chris

---

### Post by Black Serpent on 2008-11-30
I have successfully managed to:

1 - mount the ntfs partition on startup
2 - assign a share on that folder in /media/<...>

here's how:

1 - (Assume you already have samba installed and added a smb user)
2 - insert this in /etc/samba/smb.conf :
```
# [bugfix] Allow a sharing of stuff we don't actually own.
   usershare owner only = False   
```
3 - to auto-mount your partition, you'll have to modify /etc/fstab. sudo-gedit that file and enter the appropriate values by the format. I used these values: /dev/[the_device]  /media/[whatever]   auto   defaults,umask=007,gid=46 0       1
(to find out which device, use sudo fdisk -l to list the partitions.)
4 - restart, and see that your partition is auto-mounted. if it's not, then you cannot go on.
5 - run gksudo nautilus , and then goto /media. then place a share on that folder which represents the partition. it should work.
6 - connect to that share to be sure that it worked.

Good luck! write me back if it still fails.

---

